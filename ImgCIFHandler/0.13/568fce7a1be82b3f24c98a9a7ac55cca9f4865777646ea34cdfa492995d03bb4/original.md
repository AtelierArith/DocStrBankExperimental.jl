```
get_axis_vector(incif::CifContainer,axis_id,scan_id,frame_no)
```

Return the direction of `axis_id` for `frame_no` of `scan_id`. The axis vector of the nth axis up the stack is the result of applying all underlying rotations to its starting vector.
