```
CombineChannels <: Augmentor.Operation
```

## 説明

与えられた配列の最初の次元を `colortype` 型の色素に結合します。これは `ImageCore.colorview` 関数を使用します。主な違いは、グレイ画像の場合、別の色チャネルも期待されることです。

入力画像の形状は、与えられた `colortype` に適切でなければならず、分離された色チャネルは配列の最初の次元である必要があります。そうでない場合は、[`PermuteDims`](@ref) を参照してください。

## 使用法

```
CombineChannels(colortype)
```

## 引数

  * **`colortype`** : 結果の画像の色タイプ。`ColorTypes.Colorant` のサブタイプであり、与えられた画像の色チャネルと一致する必要があります。

## 参照

[`SplitChannels`](@ref), [`PermuteDims`](@ref), [`augment`](@ref)

## 例

```julia-repl
julia> using Augmentor, Colors

julia> A = rand(3, 10, 10) # 三つの色チャネル
3×10×10 Array{Float64,3}:
[...]

julia> augment(A, CombineChannels(RGB))
10×10 Array{RGB{Float64},2}:
[...]

julia> B = rand(1, 10, 10) # シングルトン色チャネル
1×10×10 Array{Float64,3}:
[...]

julia> augment(B, CombineChannels(Gray))
10×10 Array{Gray{Float64},2}:
[...]
```
