SortedVectorは、基になるデータが順序付けられた（単調増加）AbstractVectorです。

データをソート解除するようなインデックス付けは禁止されています。SortedVectorは次元軸であり、データがソートされていることを確認するチェックは行われません。重複値は許可されています。

SortedVector軸は、ClosedInterval、値、または値のベクトルでインデックス付けできます。SortedVector{Tuple}軸を使用すると、PythonのPandasパッケージやRのdata.tableパッケージの階層インデックスに似たインデックス付けが可能です。

### コンストラクタ

```julia
SortedVector(x::AbstractVector)
```

### キーワード引数

  * `x::AbstractVector` : ラップされたベクトル

### 例

```julia
v = SortedVector(collect([1.; 10.; 10:15.]))
A = AxisArray(reshape(1:16, 8, 2), v, [:a, :b])
A[ClosedInterval(8.,12.), :]
A[1., :]
A[10., :]

## 3つのキー階層を持つ階層インデックスの例

data = reshape(1.:40., 20, 2)
v = collect(zip([:a, :b, :c][rand(1:3,20)], [:x,:y][rand(1:2,20)], [:x,:y][rand(1:2,20)]))
idx = sortperm(v)
A = AxisArray(data[idx,:], SortedVector(v[idx]), [:a, :b])
A[:b, :]
A[[:a,:c], :]
A[(:a,:x), :]
A[(:a,:x,:x), :]
A[ClosedInterval(:a,:b), :]
A[ClosedInterval((:a,:x),(:b,:x)), :]
```
