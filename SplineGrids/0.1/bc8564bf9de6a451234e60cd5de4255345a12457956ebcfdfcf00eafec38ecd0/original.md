```
LocalRefinement(
    dims_refinement,
    refinement_matrices,
    refinement_indices,
    refinement_values)
```

The data for performing a local refinement; one or more refinement matrices and the to be overwritten control point values after multiplication with the refinement matrices along the specified dimensions.

## Fields

  * `dims_refinement`: The dimensions along which will be refined
  * `refinement_matrices`: The matrices that perform the refinement
  * `refinement_indices`: The indices of the control points that will be overwritten after the refinement
  * `refinement_values`: The new values of the control points that will be rewritten after refinement
