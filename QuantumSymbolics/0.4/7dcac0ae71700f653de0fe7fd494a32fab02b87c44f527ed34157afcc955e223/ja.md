量子オブジェクト（ケット、ブラ、演算子）の複素共役。

```jldoctest
julia> @op A; @ket k;

julia> conj(A)
Aˣ

julia> conj(k)
|k⟩ˣ
```
