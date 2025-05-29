Given a refinement step (by default the last refinement), add new control points that overwrite the result from the refinement matrix. These new values are chosen such that the spline geometry does not change.

## Inputs

  * `control_points`: The locally refined control points where new control points will be activated
  * `refinement_indices`: The indices in the control point grid at the `refinement_index` level which will be overwritten
  * `refinement_index`: The index of the refinement after which new control points will be activated
