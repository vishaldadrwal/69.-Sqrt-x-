# 69. Sqrt(x)
# Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well. 
# You must not # use any built-in exponent function or operator.  For example, do not use pow(x, 0.5) in c++ or x ** 0.5 in python.

# Time Complexity - O(x)	
# Space Complexity - O(1)
class Solution {
public:
    int mySqrt(int x) {
        if (x == 0) {
            return 0;
        }
        for (long long i = 1; i <= x; i++) {
            if (i * i == x) {
                return i;
            }
            else if (i * i > x) {
                return i - 1;
            }
        }
        return 0;
    }
};

# Binary Search is the preferred solution because it reduces the time complexity from O(x) to O(log x).
# Time Complexity - O(log x)
# Space Complexity - O(1)
class Solution {
public:
    int mySqrt(int x) {
        int low = 0;
        int high = x;
        int ans = 0;
        while (low <= high) {
            long long mid = low + (high - low) / 2;
            if (mid * mid == x) {
                return mid;
            }
            else if (mid * mid < x) {
                ans = mid;
                low = mid + 1;
            }
            else {
                high = mid - 1;
            }
        }
        return ans;
    }
};

