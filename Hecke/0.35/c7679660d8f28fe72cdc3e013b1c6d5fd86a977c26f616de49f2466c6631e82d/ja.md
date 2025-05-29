```
center(A::AbstractAssociativeAlgebra)
                                   -> StructureConstantAlgebra, Map

$A$の中心$C$と、$C \to A$の包含を返します。$C$自体は代数であることに注意してください。

# 例

```

jldoctest julia> A = matrix_algebra(QQ, 2);

julia> C, CtoA = center(A);

julia> C Structure constant algebra of dimension 1 over QQ ```
