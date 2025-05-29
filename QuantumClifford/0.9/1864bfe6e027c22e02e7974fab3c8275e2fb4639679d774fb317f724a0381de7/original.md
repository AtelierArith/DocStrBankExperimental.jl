Repeated tensor product of an operators or a tableau.

For `CliffordOperator`:

```jldoctest
julia> tensor_pow(CliffordOperator(sHadamard), 3)
X₁ ⟼ + Z__
X₂ ⟼ + _Z_
X₃ ⟼ + __Z
Z₁ ⟼ + X__
Z₂ ⟼ + _X_
Z₃ ⟼ + __X
```

For `PauliOperator`:

```jldoctest
julia> tensor_pow(P"IXYZ", 2)
+ _XYZ_XYZ
```

For `Tableaux`:

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

See also [`tensor`](@ref).
