```
tridiagonal_solver(a, b, c, d)
```

Tridiagonal solver

# Description

Converted into a R code from the original code of Gordon Bonan: Bonan, G. (2019). Climate Change and Terrestrial Ecosystem Modeling. Cambridge: Cambridge University Press. doi:10.1017/9781107339217

Solve for U given the set of equations R * U = D, where U is a vector of length N, D is a vector of length N, and R is an N x N tridiagonal matrix defined by the vectors A, B, C each of length N. A(1) and C(N) are undefined and are not referenced.

```
|B(1) C(1) ...  ...  ...                     |
|A(2) B(2) C(2) ...  ...                     |
```

R = |     A(3) B(3) C(3) ...                     |     |                    ... A(N-1) B(N-1) C(N-1)|     |                    ... ...    A(N)   B(N)  |

The system of equations is written as:

A*i * U*i-1 + B*i * U*i + C*i * U*i+1 = D_i

for i = 1 to N. The solution is found by rewriting the equations so that:

U*i = F*i - E*i * U*i+1

# Return

  * `Solution: U`
