演算子をブラに対して（右から）適用するシンボリックな表現。

```jldoctest
julia> @bra b; @op A;

julia> b*A
⟨b|A
```
