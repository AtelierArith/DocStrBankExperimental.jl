`Perm{T}(m::AbstractMatrix)` もし `m` が置換行列であれば、型 `T` の対応する置換を返します。省略した場合、`T` は `Int16` として扱われます。

```julia-repl
julia> Perm([0 1 0;0 0 1;1 0 0])
(1,2,3)
```
