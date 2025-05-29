```
zero_algebra([T, ] K::Field) -> AbstractAssociativeAlgebra
```

フィールド $K$ 上の代数としてゼロ環を返します。

オプションの最初の引数は代数の型を決定し、`StructureConstantAlgebra`（デフォルト）または `MatrixAlgebra` にすることができます。

# 例

```jldoctest
julia> A = zero_algebra(QQ)
Structure constant algebra of dimension 0 over QQ
```
