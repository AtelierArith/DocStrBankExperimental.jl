演算子をケトに対して（左から）作用させるシンボリックな表現。

```jldoctest
julia> @ket k; @op A;

julia> A*k
A|k⟩
```
