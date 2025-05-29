```
pipe_model!(node, var_name, threshold_value; allow_missing = false)
```

Same than `pipe_model!` but uses another variable as the reference down until a threshold value. This is used for example in the case of LiDAR measurements, where we know the cross-section (`:var_name`) is well measured down to *e.g.* 2-3cm of diameter, but should be computed below.

This function allows to compute the cross-section using the pipe model **only** for some sub-trees with values of `:var_name <= threshold_value`.

# Arguments

  * `node`: the mtg, or a specific node at which to start from.
  * `var_name`: the name of the cross-section attribute name in the nodes
  * `threshold_value`: the threshold defining the value below which the cross-section will be

re-computed using the pipe model instead of using `var_name`.

  * `allow_missing=false`: Allow missing values for `var_name`, in which case the cross-section is

recomputed using the pipe model. Please use this option only if you know why.

# Details

The node cross-section is partitioned from parent to children according to the number of leaves (*i.e.* terminal nodes) each child subtree has, unless one or more children has a `:var_name > threshold_value`. In this case the shared cross-section is the one from the parent minus the one of these nodes for which we simply use the measured value. The cross-section of the siblings with `:var_name <= threshold_value` will be shared as usual using their number of leaves. If `:var_name` of the siblings are higher than the parent value, the cross-section of the node is computed only using the number of leaves as it should not be bigger.

# Word of caution

Some tips when using this function:

  * User must ensure that `:var_name` has a value for all nodes in the mtg before calling this

version of `pipe_model!`, unless `allow_missing=true`.

  * Nodes with untrusted values should be

set to a value below the threshold value to make `pipe_model!` recompute them.
