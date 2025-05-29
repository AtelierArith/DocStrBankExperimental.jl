新しい面を、面の配列の最後に点のインデックスの配列（番号は1から始まる）を使って挿入します。

```jldoctest
julia> m = mesh(Float64);

julia> for i in 1:10 push_vertex!(m,[cos(i*pi/5), sin(i*pi/5), 0.0]) end;

julia> for i in 1:9 push_face!(m,[1,i,i+1]) end;
```
