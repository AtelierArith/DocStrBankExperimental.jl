```
as(SArray{S}, [inner_transformation])
```

`inner_transformation`（デフォルトはスカラーの恒等変換である`asℝ`）を繰り返し適用して、指定された次元の配列を作成する変換を返します。

`SMatrix`または`SVector`は、適合する次元で`SArray`の代わりに使用できます。

# 例

```julia
as(SArray{2,3}, asℝ₊, 2, 3)     # 2x3の正の数のSMatrixに変換
as(SVector{3})                   # ℝ³ → ℝ³、恒等変換だがSVector
```
