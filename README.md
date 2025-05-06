# DSA-Interview-Prep
A collaborative resource for Data Structures and Algorithms (DSA) preparation. This repository provides a structured collection of problems, ranging from brute-force to optimized solutions, along with the original problem statements.  Ideal for interview preparation and learning DSA concepts.

## Introduction

Welcome to our collaborative repository dedicated to Data Structures and Algorithms (DSA) preparation! This project aims to create a comprehensive resource for learning, practicing, and mastering DSA concepts, with a focus on interview readiness.

## Goals

* **Structured Learning:** Organize DSA problems by category (e.g., arrays, linked lists, trees, graphs) and difficulty level.
* **Comprehensive Solutions:** Provide solutions for each problem, starting with brute-force approaches and progressing to optimized solutions.
* **Problem Statements:** Include the original problem statements to provide context and ensure clarity.
* **Interview Readiness:** Focus on problems commonly asked in technical interviews.
* **Community Collaboration:** Encourage contributions from the community to expand the problem set and improve the solutions.

## Structure

The repository is organized as follows:

/
├── README.md          # This file
├── problems/          # Directory containing DSA problems
│   ├── array/           # Problems related to arrays
│   │   ├── problem1/     # Directory for a specific array problem
│   │   │   ├── problem.md    # Original problem statement
│   │   │   ├── brute_force.md  # Brute-force solution
│   │   │   └── optimized.md  # Optimized solution
│   │   └── problem2/
│   ├── linked_list/    # Problems related to linked lists
│   ├── tree/           # Problems related to trees
│   └── graph/          # Problems related to graphs
└── CONTRIBUTING.md    # Guidelines for contributing to the repository

## How to Use This Repository

1.  **Browse Problems:** Explore the `problems/` directory to find problems in specific DSA categories.
2.  **Study Solutions:** For each problem, review the `brute_force.md` and `optimized.md` files to understand different approaches.
3.  **Contribute:** See the [Contributing Guidelines](#contributing) below to learn how you can add new problems or improve existing solutions.

## Contributing

We welcome contributions from the community! Please follow these guidelines:

1.  **Fork the Repository:** Create your own fork of this repository.
2.  **Create a Branch:** Create a new branch for each problem or improvement you want to contribute (e.g., `add-two-sum-problem`, `improve-sort-solution`).
3.  **Follow the Structure:** Adhere to the repository structure described above. Create a new directory under the appropriate category in `problems/` for a new problem.
4.  **Provide Clear Solutions:**
    * Include the original problem statement in a `problem.md` file. If the problem is from a specific source (e.g., LeetCode, GeeksforGeeks), include a link.
    * Provide a brute-force solution in a `brute_force.md` file. Include code, explanation, and time/space complexity analysis.
    * Provide an optimized solution in an `optimized.md` file. Include code, explanation, and time/space complexity analysis. Explain the optimization strategy.
    * Use Markdown for all documentation. Format code blocks correctly.
5.  **Test Your Code:** Ensure your solutions are correct and well-tested.
6.  **Submit a Pull Request:** Submit a pull request to the `main` branch of this repository.
7.  **Code Review:** Your pull request will be reviewed by a maintainer. Be prepared to address any feedback.

## Example of a Problem Directory

Here's an example of how a problem directory should be structured:

problems/
└── array/
└── two_sum/
├── problem.md
├── brute_force.md
└── optimized.md
* **problem.md (two\_sum/problem.md):**

    ```markdown
    ##   Two Sum

    Given an array of integers `nums` and an integer `target`, return *indices* of the two numbers such that they add up to `target`.

    You may assume that each input would have *exactly* one solution, and you may not use the *same* element twice.

    You can return the answer in any order.

    **Example 1:**

    ```
    Input: nums = \[2,7,11,15\], target = 9
    Output: \[0,1\]
    Explanation: Because nums\[0\] + nums\[1\] == 9, we return \[0, 1\].
    ```

    **Example 2:**

    ```
    Input: nums = \[3,2,4\], target = 6
    Output: \[1,2\]
    ```

    **Example 3:**

    ```
    Input: nums = \[3,3\], target = 6
    Output: \[0,1\]
    ```

    **Constraints:**

    * `2 <= nums.length <= 10^4`
    * `-10^9 <= nums[i] <= 10^9`
    * `-10^9 <= target <= 10^9`
    * Only one valid answer exists.

    **Source:** [LeetCode (https\://leetcode.com/problems/two-sum/)](https\://leetcode.com/problems/two-sum/)
    ```

* **brute\_force.md (two\_sum/brute\_force.md):**

    ```markdown
    ##   Brute Force Solution

    The brute-force approach is to iterate through each element in the array and check if the sum of that element and any other element equals the target.

    **Code:**

    ```java
    class Solution {
        public int[] twoSum(int[] nums, int target) {
            for (int i = 0; i < nums.length; i++) {
                for (int j = i + 1; j < nums.length; j++) {
                    if (nums[i] + nums[j] == target) {
                        return new int[] { i, j };
                    }
                }
            }
            throw new IllegalArgumentException("No two elements add up to the target");
        }
    }
    ```

    **Explanation:**

    1.  The outer loop iterates through the array from index `0` to `nums.length - 1`.
    2.  The inner loop iterates from the next element (`i + 1`) to `nums.length - 1`. This avoids checking the same pair twice and doesn't use the same element twice.
    3.  Inside the inner loop, we check if the sum of the elements at indices `i` and `j` is equal to the `target`.
    4.  If the sum equals the `target`, we found the pair, and we return their indices in a new integer array.
    5.  If no such pair is found, we throw an `IllegalArgumentException`.

    **Time Complexity:** O(n^2), where n is the length of the array `nums`. This is because we have nested loops, and the inner loop iterates up to n times for each iteration of the outer loop.
    **Space Complexity:** O(1). We use a constant amount of extra space.
    ```

* **optimized.md (two\_sum/optimized.md):**

    ```markdown
    ##   Optimized Solution

    We can optimize the solution using a hash table (HashMap in Java). We iterate through the array and store each number and its index in the hash table. For each number, we check if the difference between the `target` and the current number exists in the hash table. If it does, we found the pair.

    **Code:**

    ```java
    import java.util.HashMap;
    import java.util.Map;

    class Solution {
        public int[] twoSum(int[] nums, int target) {
            Map<Integer, Integer> numMap = new HashMap<>(); // Create a HashMap to store numbers and their indices
            for (int i = 0; i < nums.length; i++) {
                int complement = target - nums[i];
                if (numMap.containsKey(complement)) {
                    return new int[] { numMap.get(complement), i };
                } else {
                    numMap.put(nums[i], i);
                }
            }
            throw new IllegalArgumentException("No two elements add up to the target");
        }
    }
    ```

    **Explanation:**

    1.  Create an empty hash table `numMap` to store each number and its index.
    2.  Iterate through the `nums` array using a standard for loop.
    3.  Calculate the `complement` (the number needed to reach the `target` with the current number).
    4.  Check if the `complement` is already in the `numMap`.
        * If it is, we found the pair. We return the index of the `complement` from the `numMap` and the current index `i` in a new integer array.
        * If it isn't, add the current number `nums[i]` and its index `i` to the `numMap`.
    5.  If no such pair is found, we throw an `IllegalArgumentException`.

    **Time Complexity:** O(n), where n is the length of the array `nums`. HashMap lookups take O(1) on average. We iterate through the array once.
    **Space Complexity:** O(n), where n is the length of the array `nums`. We store up to n elements and their indices in the hash table.
    ```

## Code Style

* Use consistent code style (e.g., Google Java Style Guide).
* Provide clear and concise variable names.
* Comment your code appropriately to explain the logic.

## Questions?

If you have any questions or need help, feel free to open an issue or start a discussion.

Happy coding!


