```
MeshData(rd::RefElemData, objects, 
         vx::AbstractVector, vy::AbstractVector,
         quadrature_type=Subtriangulation(); 
         quad_rule_face=get_1d_quadrature(rd), 
         precompute_operators=false)
```

Constructor for MeshData utilizing moment fitting. Does not guarantee positive quadrature weights, and is slower due to the use of adaptive sampling to construct 

!!! Warning: this may be deprecated or removed in future versions. 
