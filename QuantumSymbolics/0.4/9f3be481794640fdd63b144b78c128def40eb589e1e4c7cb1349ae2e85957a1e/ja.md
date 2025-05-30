演算子をケトに対して左から作用させる記号的な適用。

```jldoctest
julia> @ket k; @op A;

julia> A*k
A|k⟩
```
