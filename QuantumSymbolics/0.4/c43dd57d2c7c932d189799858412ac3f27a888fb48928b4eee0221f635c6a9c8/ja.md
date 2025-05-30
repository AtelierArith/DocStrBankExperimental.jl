演算子をブラに対して（右から）作用させるシンボリックな適用。

```jldoctest
julia> @bra b; @op A;

julia> b*A
⟨b|A
```
