演算子または表の繰り返しテンソル積。

`CliffordOperator`の場合：

```jldoctest
julia> tensor_pow(CliffordOperator(sHadamard), 3)
X₁ ⟼ + Z__
X₂ ⟼ + _Z_
X₃ ⟼ + __Z
Z₁ ⟼ + X__
Z₂ ⟼ + _X_
Z₃ ⟼ + __X
```

`PauliOperator`の場合：

```jldoctest
julia> tensor_pow(P"IXYZ", 2)
+ _XYZ_XYZ
```

`Tableaux`の場合：

```jldoctest
julia> tensor_pow(S"Z", 4)
+ Z___
+ _Z__
+ __Z_
+ ___Z

julia> s = S"+XZI
             +IZI";

julia> tensor_pow(s, 3)
+ XZ_______
+ _Z_______
+ ___XZ____
+ ____Z____
+ ______XZ_
+ _______Z_
```

詳細は[`tensor`](@ref)を参照してください。
