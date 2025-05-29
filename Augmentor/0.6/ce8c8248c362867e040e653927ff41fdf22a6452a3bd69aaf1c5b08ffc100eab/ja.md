```
GaussianBlur <: ColorOperation
```

## 説明

ガウスフィルターを使用して画像をぼかします。

## 使用法

```
GaussianBlur(k, [σ])
```

## 引数

  * **`k`** : カーネルサイズを示す `Integer` または `Integer` の `AbstractVector`。奇数の正の数でなければなりません。
  * **`σ`** : オプション。標準偏差を示す `Real` または `Real` の `AbstractVector`。正の数でなければなりません。デフォルトは `0.3 * ((k - 1) / 2 - 1) + 0.8` です。

## 例

```
using Augmentor
img = testpattern()

# k=3 と σ=1.0 を正確に使用
augment(img, GaussianBlur(3, 1.0))

# 指定された範囲から k と σ をランダムに選択
augment(img, GaussianBlur(3:2:7, 1.0:0.1:2.0))
```
