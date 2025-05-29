```
Resize <: Augmentor.ImageOperation
```

## 説明

画像を固定の事前指定されたピクセルサイズにリスケールします。

この操作は、ソース画像のアスペクト比を保持するための措置を講じません。代わりに、元の画像は単に指定された寸法にリサイズされます。これは、すべての画像が正確に同じサイズである必要がある場合に便利です。

## 使用法

```
Resize(; height=64, width=64)

Resize(size)

Resize(size...)
```

## 引数

  * **`size`** : 各次元の出力サイズをピクセルで示す `NTuple` または `Int` の `Vararg`。

## 参照

[`CropSize`](@ref), [`augment`](@ref)

## 例

```julia
using Augmentor
img = testpattern()

augment(img, Resize(30, 40))
```
