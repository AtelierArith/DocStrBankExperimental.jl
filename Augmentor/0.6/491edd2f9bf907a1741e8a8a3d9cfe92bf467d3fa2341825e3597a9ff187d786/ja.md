```
FlipY <: Augmentor.AffineOperation
```

## 説明

各ピクセル列のy順を反転させます。別の言い方をすると、画像をx軸でミラーリングする、または画像を垂直にミラーリングすることになります。

パラメータ`p`を使用して作成された場合、この操作は`Either(p=>FlipY(), 1-p=>NoOp())`に持ち上げられます。ここで、`p`は`FlipY`を適用する確率を示し、`1-p`は[`NoOp`](@ref)を適用する確率を示します。詳細については[`Either`](@ref)のドキュメントを参照してください。

## 使用法

```
FlipY()

FlipY(p)
```

## 引数

  * **`p::Number`** : オプション。操作を適用する確率。範囲は[0,1]でなければなりません。

## 参照

[`FlipX`](@ref), [`Either`](@ref), [`augment`](@ref)

## 例

```jldoctest
julia> using Augmentor

julia> img = [200 150; 50 1]
2×2 Matrix{Int64}:
 200  150
  50    1

julia> img_new = augment(img, FlipY())
2×2 Matrix{Int64}:
  50    1
 200  150
```
