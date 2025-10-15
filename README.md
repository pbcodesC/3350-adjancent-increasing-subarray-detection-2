# 3350-adjancent-increasing-subarray-detection-2
daily leetcode challange 
#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    int maxIncreasingSubarrays(vector<int>& nums) {
        int n = nums.size();
        if (n < 2) return 0;

        int prev = 0, curr = 1, ans = 0;

        for (int i = 1; i < n; i++) {
            if (nums[i] > nums[i - 1]) {
                curr++;
            } else {
                prev = curr;
                curr = 1;
            }
            ans = max(ans, min(prev, curr));
            ans = max(ans, curr / 2);
        }

        return ans;
    }
};
