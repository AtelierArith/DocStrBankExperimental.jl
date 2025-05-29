```
H8sphere(radius::T, nrefine::IT) where {T<:Number, IT<:Integer}

Create a mesh of 1/8 of the sphere of "radius". The  mesh will consist of
four hexahedral elements if "nrefine==0",  or more if "nrefine>0".
"nrefine" is the number of bisections applied  to refine the mesh.
```
