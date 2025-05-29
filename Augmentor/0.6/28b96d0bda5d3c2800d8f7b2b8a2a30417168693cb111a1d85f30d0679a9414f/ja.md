```
Crop <: Augmentor.ImageOperation
```

## 説明

指定されたピクセル範囲によって示される領域を切り取ります。

例えば、操作 `Crop(5:100, 2:10)` は、左上隅の `x=2` と `y=5` から始まり、右下隅の `x=10` と `y=100` で終わる矩形の切り取りを示します。画像が配列に格納される方法から、y軸が最初に指定されることがわかります。したがって、提供された軸の範囲の順序は、配列の次元の順序を反映する必要があります。

## 使用法

```
Crop(indices)

Crop(indices...)
```

## 引数

  * **`indices`** : 各配列次元の切り取り範囲を示す `UnitRange` の `NTuple` または `Vararg`。これは `view` の軸が指定される方法に非常に似ています。

## 参照

[`CropNative`](@ref), [`CropSize`](@ref), [`CropRatio`](@ref), [`augment`](@ref)

## 例

```julia-repl
julia> using Augmentor

julia> img = testpattern()
300×400 Array{RGBA{N0f8},2}:
[...]

julia> augment(img, Crop(1:30, 361:400)) # 右上隅を切り取る
30×40 Array{RGBA{N0f8},2}:
[...]
```
