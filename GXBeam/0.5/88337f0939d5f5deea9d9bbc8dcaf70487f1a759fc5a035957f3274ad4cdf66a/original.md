```
correlate_eigenmodes(C)
```

Return the permutation and the associated corruption index vector which associates eigenmodes from the current iteration with those of the previous iteration given the correlation matrix `C`.

The correlation matrix can take one of the following forms (in order of preference):

  * `C = U_p*M*V`
  * `C = U*M_p*V_p`
  * `C = V_p'*V`
  * `C = V'*V_p`

where `U` is a matrix of conjugated left eigenvectors, `M` is the system mass matrix, `V` is a matrix of right eigenvectors, and `()_p` indicates a variable from the previous iteration.

Note that the following two forms of the correlation matrix seem to be significantly inferior to their counterparts listed above: `C = U*M*V_p` and `C = U_p*M_p*V`. This is likely due to the way in which the left eigenvector matrix is calculated.

The corruption index is the largest magnitude in a given row of `C` that was not chosen divided by the magnitude of the chosen eigenmode.  It is most meaningful when using one of the forms of the correlation matrix that uses left eigenvectors since correct eigenmodes will have magnitudes close to 1 and incorrect eigenmodes will have magnitudes close to 0.

If the new mode number is already assigned, the next highest unassigned mode number is used.  In this case a corruption index higher than 1 will be returned, otherwise the values of the corruption index will always be bounded by 0 and 1.

See "New Mode Tracking Methods in Aeroelastic Analysis" by Eldred, Vankayya, and Anderson.
