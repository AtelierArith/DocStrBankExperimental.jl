```
CloughTocher2DInterpolator(points, values; kwargs...)
```

与えられた `points` と `values` のクラウドに対して Clough-Tocher 2D 補間器を設定します。

`points` は「コンポーネント主要順序」でデータを保持します。例えば、点 `(0,0), (1,0), (0,1)` を持つ単一の三角形は `points = [ 0,0, 1,0, 0,1 ]` としてエンコードされます。

利用可能なキーワード引数：

  * fill_value=NaN: 入力点の凸包の外にある要求された点を埋めるために使用される値。
  * tol=1e-6: 勾配推定のための許容誤差。
  * maxiter=400: 勾配推定における最大反復回数。
  * rescale=false: 補間を行う前に点を単位立方体に再スケールします。これは、入力次元のいくつかが非同次単位を持ち、桁数が大きく異なる場合に便利です。

# 例

```julia
points  = [0,0, 0,1, 1,0, 1,1, 2,0, 2,1]
ipoints = [0.5,0.5, 1.5,0.5]

# 実数
data   = [1.0, 2.0, 3.0, 4.0, 5.0, 6.0]
interp = CloughTocher2DInterpolator(points, data)
interp(ipoints)

# 複素数
data   = [1.0+2.0im, 2.0+3.0im, 3.0-1.0im, 4.0-0.5im, 5.0-3.0im, 6.0+5.0im]
interp = CloughTocher2DInterpolator(points, data)
interp(ipoints)

# 事前に確保された配列にデータを補間する（必要に応じてサイズ変更されます）
result = zeros(eltype(data), length(data))
interp(ipoints, result)
```
