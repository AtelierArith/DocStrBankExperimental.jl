```
FlipX <: Augmentor.AffineOperation
```

## 説明

各ピクセル行のx順序を反転させます。別の言い方をすれば、画像をy軸で鏡映しにする、または画像を水平方向に鏡映しにすることです。

パラメータ`p`を使用して作成された場合、この操作は`Either(p=>FlipX(), 1-p=>NoOp())`に持ち上げられます。ここで、`p`は`FlipX`を適用する確率を示し、`1-p`は[`NoOp`](@ref)を適用する確率を示します。詳細については[`Either`](@ref)のドキュメントを参照してください。

## 使用法

```
FlipX()

FlipX(p)
```

## 引数

  * **`p::Number`** : オプション。操作を適用する確率。範囲は[0,1]でなければなりません。

## 参照

[`FlipY`](@ref), [`Either`](@ref), [`augment`](@ref)

## 例

```jldoctest
julia> using Augmentor

julia> img = [200 150; 50 1]
2×2 Matrix{Int64}:
 200  150
  50    1

julia> img_new = augment(img, FlipX())
2×2 Matrix{Int64}:
 150  200
   1   50
```
