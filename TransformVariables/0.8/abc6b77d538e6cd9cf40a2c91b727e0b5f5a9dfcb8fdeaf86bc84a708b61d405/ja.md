```
as(Array, [transformation], dims...)
as(Array, [transformation], dims)
```

指定された `dims` を持つ配列を作成するために、`transformation`（スカラーに対する恒等変換である `asℝ` がデフォルト）を繰り返し適用する変換を返します。

`Matrix` または `Vector` は、適合する次元で `Array` の代わりに使用できます。

# 例

```julia
as(Array, asℝ₊, 2, 3)           # 正の数の2x3行列に変換
as(Vector, 3)                   # ℝ³ → ℝ³, 恒等
```
