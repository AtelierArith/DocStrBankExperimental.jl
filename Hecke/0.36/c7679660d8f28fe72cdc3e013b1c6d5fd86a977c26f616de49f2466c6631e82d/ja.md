```
center(A::AbstractAssociativeAlgebra)
                                   -> StructureConstantAlgebra, Map

$A$の中心$C$と包含$C \to A$を返します。$C$自体は代数であることに注意してください。

# 例

```

jldoctest julia> A = matrix_algebra(QQ, 2);

julia> C, CtoA = center(A);

julia> C QQ上の次元1の構造定数代数 ```
