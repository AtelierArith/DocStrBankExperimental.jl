```
Rotate <: Augmentor.AffineOperation
```

## 説明

指定された `degree` の方向に画像を回転させます。この操作はアフィン変換としてのみ実行でき、一般的にパイプラインの他の操作もアフィン形式を使用することになります（もしそれがある場合）。

特別なケースの回転（例: [`Rotate90`](@ref)）とは対照的に、`Rotate` 型は任意の度数を表すことができます。常に画像の中心を中心に回転を行います。この操作を [`CropNative`](@ref) と組み合わせる際に特に便利です。

## 使用法

```
Rotate(degree)
```

## 引数

  * **`degree`** : 回転角度を度で示す `Real` または `Real` の `AbstractVector`。ベクトルが提供されると、操作が適用されるたびにランダムな要素がサンプリングされます。

## 参照

[`Rotate90`](@ref), [`Rotate180`](@ref), [`Rotate270`](@ref), [`CropNative`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor
img = testpattern()

# 正確に45度回転
augment(img, Rotate(45))

# 10度から20度の間で上向きに回転
augment(img, Rotate(10:20))

# 指定された5つの度数のいずれかで回転
augment(img, Rotate([-10, -5, 0, 5, 10]))
```
