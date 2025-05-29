```
assemble!(A::AbstractAssembler, dofs::AbstractVector{Int}, Ke::AbstractMatrix)
assemble!(A::AbstractAssembler, dofs::AbstractVector{Int}, Ke::AbstractMatrix, fe::AbstractVector)
```

要素剛性行列 `Ke`（およびオプションの力ベクトル `fe`）を、要素自由度 `dofs` に基づいて、グローバル剛性（および力）行列 `A` に組み込みます。

これは `K[dofs, dofs] += Ke` および `f[dofs] += fe` に相当しますが、より効率的です。ここで、`K` はグローバル剛性行列、`f` はグローバル力/残差ベクトルです。
