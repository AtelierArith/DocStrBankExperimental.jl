演算子または表の間のテンソル積。

CiffordOperators間のテンソル積：

```jldoctest
julia> tensor(CliffordOperator(sCNOT), CliffordOperator(sCNOT))
X₁ ⟼ + XX__
X₂ ⟼ + _X__
X₃ ⟼ + __XX
X₄ ⟼ + ___X
Z₁ ⟼ + Z___
Z₂ ⟼ + ZZ__
Z₃ ⟼ + __Z_
Z₄ ⟼ + __ZZ
```

PauliOperators間のテンソル積：

```jldoctest
julia> tensor(P"-IXYZ", P"iIXYZ")
-i_XYZ_XYZ
```

表間のテンソル積：

```jldoctest
julia> s = S"-XX
             +ZZ";

julia> tensor(s, s, s)
- XX____
+ ZZ____
- __XX__
+ __ZZ__
- ____XX
+ ____ZZ

julia> s = S"+XZI
             -IZI";

julia> tensor(s, s)
+ XZ____
- _Z____
+ ___XZ_
- ____Z_
```

[`tensor_pow`](@ref)も参照してください。
