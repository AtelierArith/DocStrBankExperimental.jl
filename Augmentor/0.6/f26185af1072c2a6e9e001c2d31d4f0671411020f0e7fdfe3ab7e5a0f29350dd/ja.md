```
CacheImage <: Augmentor.ImageOperation
```

## 説明

画像の現在の状態を作業メモリに書き込みます。オプションとして、ユーザーは画像を書き込むための事前に割り当てられた `buffer` を指定することができます。`buffer` が提供される場合、それは正しいサイズと eltype でなければなりません。

事前に割り当てられた `buffer` がなくても、画像をキャッシュすることが有益な場合があります。そのようなシナリオの例は、弾性歪みの後にいくつかのアフィン変換を連鎖させる場合です。なぜなら、遅延実行するにはネストされた補間が必要だからです。

## 使用法

```
CacheImage()

CacheImage(buffer)
```

## 引数

  * **`buffer`** : オプション。適切なサイズと eltype の事前に割り当てられた `AbstractArray`。

## 参照

[`augment`](@ref)

## 例

```julia
using Augmentor

# 弾性歪みの後にキャッシュを強制するパイプラインを作成
pl = ElasticDistortion(3,3) |> CacheImage() |> Rotate(-10:10) |> ShearX(-5:5)

# 弾性歪みの出力を割り当てられた
# 20x20 Matrix{Float64} にキャッシュします。この場合、入力画像も
# 20x20 Matrix{Float64} であると仮定しています。
pl = ElasticDistortion(3,3) |> CacheImage(zeros(20,20)) |> Rotate(-10:10)

# 上記と同じ効果を持つ便利な構文。
pl = ElasticDistortion(3,3) |> zeros(20,20) |> Rotate(-10:10)
```
