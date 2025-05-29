Complex conjugate of quantum objects (kets, bras, operators).

```jldoctest
julia> @op A; @ket k;

julia> conj(A)
Aˣ

julia> conj(k)
|k⟩ˣ
```
