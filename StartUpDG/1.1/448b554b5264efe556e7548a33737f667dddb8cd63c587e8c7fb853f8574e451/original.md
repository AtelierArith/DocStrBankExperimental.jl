```
RefElemData(elem::Wedge, approximation_type::Polynomial, N;
            quad_rule_vol=quad_nodes(elem, N),
            quad_rule_face_quad=quad_nodes(Quad(), N), 
            quad_rule_face_tri=quad_nodes(Tri(), N), 
            quad_rule_face=(quad_rule_face_quad, quad_rule_face_tri),
            Nplot=10)
```

Builds operators for prisms/wedges
