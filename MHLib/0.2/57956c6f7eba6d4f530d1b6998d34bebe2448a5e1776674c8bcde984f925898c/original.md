```
element_added_delta_eval!(SubsetVectorSolution)
```

Element `x[sel-1]`` was added to a solution, if feasible update further solution data,  else revert.

This is a helper function for delta-evaluating solutions when searching a neighborhood  that needs to be overloaded for a concrete problem. It can be assumed that the solution was in a correct state with a valid objective value  in `obj_val` *before* the already applied move, `obj_val_valid` therefore is true. The default implementation just calls `invalidate!()` and returns true.

  * `update_obj_val`: if set, the objective value should also be updated or invalidate    needs to be called
  * `allow_infeasible`: if set and the solution is infeasible, the move is nevertheless    accepted and the update of other data done

Returns true if feasible, false if infeasible.
