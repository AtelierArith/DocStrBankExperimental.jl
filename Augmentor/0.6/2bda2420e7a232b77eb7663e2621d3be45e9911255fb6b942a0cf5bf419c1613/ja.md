```
ShearX <: Augmentor.AffineOperation
```

## 説明

指定された `degree` に対して画像を水平方向にせん断します。この操作はアフィン変換としてのみ実行でき、一般的にパイプラインの他の操作もアフィン形式を使用することになります（もしそれがある場合）。

常に画像の中心を基準に変換を行います。この操作を [`CropNative`](@ref) と組み合わせる際に特に便利です。

## 使用法

```
ShearX(degree)
```

## 引数

  * **`degree`** : せん断角度を度で示す `Real` または `Real` の `AbstractVector`。ベクトルが提供されると、操作が適用されるたびにランダムな要素がサンプリングされます。

## 参照

[`ShearY`](@ref), [`CropNative`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor
img = testpattern()

# 正確に5度水平方向にせん断
augment(img, ShearX(5))

# 右に10度から20度の間で水平方向にせん断
augment(img, ShearX(10:20))

# 指定された5つの角度のうちの1つで水平方向にせん断
augment(img, ShearX([-10, -5, 0, 5, 10]))
```
