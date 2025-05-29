```
block_tridiagonal_inverse(A, B, C)
```

Compute the inverse of a block tridiagonal matrix.

# Arguments

  * `A`: Lower diagonal blocks.
  * `B`: Main diagonal blocks.
  * `C`: Upper diagonal blocks.

# Returns

  * `λii`: Diagonal blocks of the inverse.
  * `λij`: Off-diagonal blocks of the inverse.

# Notes: This implementation is from the paper:

"An Accelerated Lambda Iteration Method for Multilevel Radiative Transfer” Rybicki, G.B., and Hummer, D.G., Astronomy and Astrophysics, 245, 171–181 (1991), Appendix B.
