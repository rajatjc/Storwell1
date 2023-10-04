**Embedded Software Engineer Quiz**

Please submit answers by creating a public repo on Github or Bitbucket and sharing the URL of the repo. Please do not submit answers in any other format. If you are submitting your application on our website, please use the cover letter field to include a document that contains the link to your git repo. There are two questions in this quiz; please see page 2 for the second question.

**Q1)** Consider that you have a rectangular piece of paper of arbitrary dimensions N by M (where N and M are positive integers). You also have a pair of scissors which can cut perfectly straight with no loss of paper. You wish to reduce the original piece of paper into a series of perfect squares of paper, making the largest possible squares, and using all of the paper provided. Write a function in C that takes the inputs N and M and returns the series of squares that can be made out of that piece of paper. No fractional squares, i.e., no square should be less than 1 in length and width.

Some examples:
- Input: N = 6, M = 5
  Output: 5x5, 1x1, 1x1, 1x1, 1x1, 1x1

- Input: N = 1, M = 1
  Output: 1x1

- Input: N = 9, M = 9
  Output: 9x9

```
#include <stdio.h>

void findSquares(int N, int M) {
    while (1) {
        // If N and M are equal, a square of size N or M can be cut.
        if (N == M) {
            printf("%dx%d, ", N, M);
            return;
        }

        // If either N or M is 1, the remaining paper is a series of 1x1 squares.
        if (N == 1 || M == 1) {
            int h = (N > M) ? N : M;
            for (int i = 0; i < h; i++) {
                printf("1x1, ");
            }
            return;
        }

        // Find the minimum dimension and cut a square of that size.
        int min_dim = (N < M) ? N : M;
        printf("%dx%d, ", min_dim, min_dim);

        // Update the dimensions.
        if (N < M) {
            M -= min_dim;
        } else {
            N -= min_dim;
        }
    }
}

int main() {
    int N, M;
    printf("Enter the dimensions N and M: ");
    scanf("%d%d", &N, &M);
    printf("Series of squares: ");
    findSquares(N, M);
    printf("\n");
    return 0;
}
```
