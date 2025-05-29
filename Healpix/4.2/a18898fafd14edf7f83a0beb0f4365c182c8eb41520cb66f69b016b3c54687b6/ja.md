```
struct HealpixMap{T, O <: Order, AA <: AbstractArray{T, 1}} <: AbstractHealpixMap{T}
```

ヒールピックスマップ。型 `T` はマップ内のピクセルの値に使用され、任意のもので構いません（文字列でも可！）。型 `O` はピクセルの順序を指定するために使用され、`RingOrder` または `NestedOrder` のいずれかになります。型 `AA` はピクセルの配列を格納するために使用され、一般的な型には `Vector`、`CUArray`、`SharedArray` などがあります。

`HealpixMap` 型には以下のフィールドが含まれます：

  * `pixels`: ピクセルの配列
  * `resolution`: `Resolution` オブジェクトのインスタンス

次のいずれかの形式を使用してマップを構築できます：

  * `HealpixMap{T, O, AA}(arr)` および `HealpixMap{T, O, AA}(nside::Number)` は `AA` をベース型として使用します
  * `HealpixMap{T, O}(arr)` および `HealpixMap{T, O}(nside::Number)` は `Array{T, 1}` をベース型として使用します

# 例

次の例は、`NSIDE=32` の `RING` 順序で、1から始まる整数値を含むマップを作成します：

```
mymap = Healpix.HealpixMap{Int64, Healpix.RingOrder}(1:Healpix.nside2npix(32))
```

範囲を配列に変換するために `collect` の呼び出しが必要です。

この例は、`NESTED` 順序で、`NSIDE=64` のゼロで埋められたマップを作成します：

```
mymap = Healpix.HealpixMap{Float64, Healpix.NestedOrder}(64)
```

最後に、次の例は `SharedArray` の使用方法を示しています：

```
using SharedArrays

# すべてのピクセルがゼロに設定されたマップを作成
mymap = Healpix.HealpixMap{Float64, Healpix.NestedOrder, SharedArray{Float64, 1}}(64)

# マップを作成し、SharedArray でピクセル値を初期化
pixels = SharedArray{Int64, 1}(1:12 |> collect)
mymap = Healpix.HealpixMap{Int64, Healpix.RingOrder, SharedArray{Int64, 1}}(m)
```
