```
PermuteDims <: Augmentor.Operation
```

## 説明

与えられた配列の次元を、事前に定義された順序 `perm` で並べ替えます。この操作は、次元の順序がデフォルトの「ジュリア」レイアウト（以下に説明）とは異なる必要がある場合に特に便利です。

Augmentorは、与えられた画像が縦優先レイアウトであることを期待しており、色は要素の型自体にエンコードされています。しかし、多くの深層学習フレームワークは、異なる順序での入力を要求します。たとえば、別々の色チャネルが第三次元にエンコードされることが期待されるのは珍しくありません。

## 使用法

```
PermuteDims(perm)

PermuteDims(perm...)
```

## 引数

  * **`perm`** : 使用する具体的な次元の順序。`Vararg{Int}` または `Int` の `NTuple` として指定する必要があります。`perm` の長さは、その操作に対する期待される入力画像の次元数と一致する必要があります。

## 参照

[`SplitChannels`](@ref), [`CombineChannels`](@ref), [`augment`](@ref)

## 例

```julia-repl
julia> using Augmentor, Colors

julia> A = rand(10, 5, 3) # 幅=10、高さ=5、色チャネル=3
10×5×3 Array{Float64,3}:
[...]

julia> img = augment(A, PermuteDims(3,2,1) |> CombineChannels(RGB))
5×10 Array{RGB{Float64},2}:
[...]

julia> img2 = testpattern()
300×400 Array{RGBA{N0f8},2}:
[...]

julia> B = augment(img2, SplitChannels() |> PermuteDims(3,2,1))
400×300×4 Array{N0f8,3}:
[...]
```
