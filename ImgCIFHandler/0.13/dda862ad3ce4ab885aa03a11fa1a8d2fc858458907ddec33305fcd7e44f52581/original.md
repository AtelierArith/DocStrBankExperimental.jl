```
get_axis_vector(incif::CifContainer,axis_id,axis_vals)
```

Return the direction of `axis_id` when the axes take values given by `axis_vals`, which is a dictionary of name=>setting. The axis vector of the nth axis up the stack is the result of applying all underlying rotations to its starting vector.
