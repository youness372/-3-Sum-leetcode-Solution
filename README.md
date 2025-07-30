# LeetCode Solution: Three Sum (Problem 15)

# - *Overview*: 

This repository contains my Python solution for the "3Sum" problem on LeetCode. The problem asks you to find all unique 
triplets [a, b, c] in a given array nums such that a + b + c = 0. The solution must not contain duplicate triplets.

Problem Description : 
Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that   i != j, i != k, 
and j != k, and nums[i] + nums[j] + nums[k] == 0.  ( https://leetcode.com/problems/3sum/description/).   

Notice that the solution set must not contain duplicate triplets.

# - *Example* 🧪 :   
- input -> `nums = [-1,0,1,2,-1,-4]`     
- output -> `[[-1, -1, 2], [-1, 0, 1]]`    

<img width="755" height="403" alt="Untitled Diagram drawio" src="https://github.com/user-attachments/assets/e13ec93d-5c0d-44a9-a10c-0038f286d213" />


# - *⛓️‍💥 My Solution Approach*  : 

My solution to the 3Sum problem leverages a combination of sorting and the Two-Pointers 
technique to efficiently find all unique triplets that sum to zero.

Here's a breakdown of the steps:

- *Input Validation (Optional but good practice)* :

  I've included checks for the input array's length and the range of numbers, returning an `"Error"` 
  string if constraints aren't met.

    - Note: LeetCode typically assumes valid input based on constraints, so this part is more for robust local use.
  
- *Sorting the Array* :

  The first crucial step is to sort the input array `nums` in non-decreasing order. This enables
  the efficient use of the Two-Pointers technique and simplifies handling duplicate triplets.


- *Iterating and Fixing the First Element* :
  - I iterate through the sorted array with an outer loop, fixing one element `nums[i]` at a time. This `nums[i]` will be the first element of our potential triplet.
  - *Skipping Duplicates for* `nums[i]` : To avoid duplicate triplets, if the current `nums[i]` is the same as the previous `nums[i-1]` (and `i > 0`), I skip it using
     `continue`. This ensures we only process unique starting elements for our triplets.
    
-  *Two-Pointers Technique* :
    - For each fixed `nums[i]`, the problem reduces to finding two other numbers in the remaining part of the array that sum to `(-nums[i])`. This is a classic `"Two Sum"`
       variation on a sorted array.

    - Two pointers, `left` (starting at `i + 1`) and `right` (starting at the end of the array `len(nums) - 1`), are initialized.

    - The `while left < right` loop continues as long as the pointers haven't crossed.

- *Calculating the Sum and Adjusting Pointers* :

  - Inside the `while loop` , I calculate `total = nums[i] + nums[left] + nums[right]` .

  - If `total == 0`:

    - A valid triplet is found! Add `[nums[i], nums[left], nums[right]]`  to the result list.

    - Skipping Duplicates for `left`  and `right`  pointers past any duplicate values. This is done with `while left < right and nums[left] == nums[left + 1]: left += 1`
       and similarly for `right`.

    - Finally, `left` is incremented and `right` is decremented to continue the search for other triplets.

  - If `total < 0`:

    - The sum is too small. To get closer to zero, we need a larger number. So, increment the `left` pointer (`left += 1`).

  - If `total > 0`:

    - The sum is too large. To get closer to zero, we need a smaller number. So, decrement the `right` pointer (`right -= 1`).

 - *Return Result*  :
   - After the loops Complete, The `result` list contains all unique triples that sum to zero.

# -*⌛ Time and Space Complexity* :  
- Time Complexity: `O(N^2)`

  - Sorting takes `O(NlogN)`.

  - The outer loop runs `N` times.

  - The inner Two-Pointers loop runs `O(N)` times on average.

  - The duplicate skipping steps take constant time within the loop.

  - Therefore, the dominant factor is `O(NcdotN)=O(N^2)`.

- Space Complexity: `O(logN)` to $$O(N)$$

  - Sorting typically uses `O(logN)` to `O(N)` space depending on the implementation (e.g., Timsort in Python).

  - The `result`  list stores the triplets, which can take up to `O(N^2)` space in the worst. However, if we're only
    considering the auxiliary space used beyond the output, it's usually considered `O(1)` if the output space isn't
     counted. In competitive programming, output space is often excluded from space complexity analysis unless explicitly stated.

# - *How to Run* :   
- *Clone This repostitory* :
  
      git clone [(https://github.com/youness372/-3-Sum-leetcode-Solution)]
      cd [three_sum_solution]
- Open the `three_sum_solution.ipynb `.

- You can test the function by adding calls at the end of the file:

      # Example usage:
      print(threeSum([-1, 0, 1, 2, -1, -4]))
      print(threeSum([0, 1, 1]))
      print(threeSum([0, 0, 0]))

-  # Thanks For your Time .

<img width="1400" height="700" alt="image" src="https://github.com/user-attachments/assets/7ab302eb-4d60-4881-a8a4-7110f7abf2ff" />
