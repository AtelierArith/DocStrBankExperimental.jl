```
RoundingSettings(settings...)
```

Settings for the rounding procedure:

1. Finding the kernel

      * `kernel_errbound`: (default: `1e-10`) the allowed error for the kernel vectors. That is, the maximum entry of Xv is in absolute value at most this
      * `kernel_round_errbound`: (default: `1e-15`) the maximum allowed error when rounding the reduced row-echelon form entrywise
      * `kernel_use_primal`: (default: `true`) use the primal solution to find the kernel vectors  (otherwise, use an SVD of the dual solution)
      * `kernel_lll`: (default: `false`) if true, use the LLL algorithm to find the nullspace of the kernel. Otherwise, use the reduced row-echelon form to find kernel vectors.
      * `kernel_bits`: (default: `1000`) the maximum number of bits to be used in the LLL algorithm (for finding relations or finding the entries of the RREF)
2. Reducing the kernel vectors

      * `reduce_kernelvectors`: (default: `true`) apply the reduction step or not
      * `reduce_kernelvectors_cutoff`: (default: `400`) do reduction on the full matrix if its size is at most this cutoff. Otherwise do it on a submatrix
      * `reduce_kernelvectors_stepsize`: (default: `200`) the number of extra columns to take into account in each iteration of the reduction step
3. Transforming the problem and the solution

      * `unimodular_transform`: (default: `true`) use a unimodular transform obtained in the reduction step
      * `normalize_transformation`: (default: `true`) multiply by a diagonal matrix to get an integer transformation for the problem (for problems over QQ)
4. Finding an approximate solution in the field

      * `regularization`: (default: `1e-20`) use this regularization for solving the extended system
      * `approximation_decimals`: (default: `40`) Approximate the numerical solution using this many digits, entrywise
5. Rounding the solution to the affine space of constraints

      * `redundancyfactor`: (default: `10`) take at least this times the number of constraints columns as potential pivots
      * `pseudo`: (default: `true`) use the psuedo inverse for rounding (this may give solutions with larger bitsize than needed)
      * `pseudo_columnfactor`: (default: `1.05`) For a system of r rows, use r * pseudo_columnfactor number of columns for the pseudo inverse
      * `extracolumns_linindep`: (default: `false`) if true, take the extra columns linearly independent of each other (otherwise, random columns)
