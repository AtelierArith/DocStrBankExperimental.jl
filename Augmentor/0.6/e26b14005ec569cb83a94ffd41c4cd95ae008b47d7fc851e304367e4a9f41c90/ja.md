```
ColorJitter <: ColorOperation
```

## 説明

画像の明るさとコントラストを、`α * image[i] + β * M`という式に従って調整します。ここで、`M`は`mean(image)`または最大強度値です。

## 使用法

```
ColorJitter()
ColorJitter(α, β; [usemax])
```

## 引数

  * **`α`** : コントラスト調整のための係数を示す`Real`または`Real`の`AbstractVector`。デフォルトは`0.8:0.1:1.2`です。
  * **`β`** : 明るさ調整のための係数を示す`Real`または`Real`の`AbstractVector`。デフォルトは`-0.2:0.1:0.2`です。
  * **`usemax::Bool`**: オプション。`true`の場合、明るさは最大強度値によって調整されます。それ以外の場合は画像の平均が使用されます。デフォルトは`true`です。

## 例

```
using Augmentor
img = testpattern()

# コントラストに正確に1.2を使用し、明るさには0.5または0.8のいずれかを使用
augment(img, ColorJitter(1.2, [0.5, 0.8]))

# 指定された範囲から係数をランダムに選択
augment(img, ColorJitter(0.8:0.1:2.0, 0.5:0.1:1.1))
```
