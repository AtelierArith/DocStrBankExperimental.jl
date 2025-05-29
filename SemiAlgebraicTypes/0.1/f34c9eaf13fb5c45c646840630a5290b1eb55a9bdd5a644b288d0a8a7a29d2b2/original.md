Insert a new face with the array of indices of the points (numbering starting at 1) at the end of the face array.

```jldoctest
julia> m = mesh(Float64);

julia> for i in 1:10 push_vertex!(m,[cos(i*pi/5), sin(i*pi/5), 0.0]) end;

julia> for i in 1:9 push_face!(m,[1,i,i+1]) end;
```
