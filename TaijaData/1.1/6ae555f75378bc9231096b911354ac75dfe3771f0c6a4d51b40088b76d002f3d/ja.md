```
load_linearly_separable(n=250; seed=data_seed)
```

線形分離可能な合成データを読み込みます。

!!! note
    これは、特定のパラメータとシードを [`data_seed`](@ref) に設定して [`load_blobs`](@ref) 関数を呼び出します。線形分離可能性と再現性を確保するために、`seed` キーワード引数を設定しても効果はありません。必要に応じて、異なるパラメータで直接 [`load_blobs`](@ref) を使用することで、より柔軟性を持たせることができます。

