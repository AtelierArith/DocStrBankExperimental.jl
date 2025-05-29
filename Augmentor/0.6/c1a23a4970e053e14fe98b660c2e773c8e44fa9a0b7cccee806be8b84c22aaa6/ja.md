```
SplitChannels <: Augmentor.Operation
```

## 説明

与えられた画像の色チャネルを `ImageCore.channelview` 関数を使用して分割します。これにより、色のための新しい配列次元が前に作成されます。`ImageCore.channelview` と対照的に、グレイ画像の場合は新しい次元も生成されます。

この操作は、色チャネルを分離することが多いトレーニングアルゴリズムのために画像を準備するために、主にパイプラインの最後で [`PermuteDims`](@ref) と組み合わせて使用されます。

## 使用法

```
SplitChannels()
```

## 関連項目

[`PermuteDims`](@ref), [`CombineChannels`](@ref), [`augment`](@ref)

## 例

```julia-repl
julia> using Augmentor

julia> img = testpattern()
300×400 Array{RGBA{N0f8},2}:
[...]

julia> augment(img, SplitChannels())
4×300×400 Array{N0f8,3}:
[...]

julia> augment(img, SplitChannels() |> PermuteDims(3,2,1))
400×300×4 Array{N0f8,3}:
[...]
```
