```
RefElemData(elem::Line, approximation_type, N;
            quad_rule_vol = quad_nodes(elem, N+1))
RefElemData(elem, approximation_type, N;
            quad_rule_vol = quad_nodes(elem, N),
            quad_rule_face = quad_nodes(face_type(elem), N))
```

Constructor for `RefElemData` for different element types.
