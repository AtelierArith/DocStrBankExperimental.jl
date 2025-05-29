シンボリック演算子のベクトル化。

```jldoctest
julia> @op A; @op B;

julia> vec(A)
|A⟩⟩

julia> vec(A+B)
|A⟩⟩+|B⟩⟩
```
