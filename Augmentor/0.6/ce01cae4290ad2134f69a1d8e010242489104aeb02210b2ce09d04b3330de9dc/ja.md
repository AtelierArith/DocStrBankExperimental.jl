```
ConvertEltype <: Augmentor.Operation
```

## 説明

与えられた配列/画像の要素型を指定された `eltype` に変換します。この操作は、特にカラー画像をグレースケールに変換する（またはその逆）ために便利です。ただし、この操作はカラータイプに特有のものではなく、数値配列（例：分離されたチャンネルを持つもの）にも使用できます。

これは要素ごとの変換関数であるため、カラー チャンネルを結合または分離するためには使用できません。その目的には [`SplitChannels`](@ref) または [`CombineChannels`](@ref) を使用してください。

## 使用法

```
ConvertEltype(eltype)
```

## 引数

  * **`eltype`** : 結果の配列/画像の要素型。

## 参照

[`CombineChannels`](@ref), [`SplitChannels`](@ref), [`augment`](@ref)

## 例

```julia-repl
julia> using Augmentor, Colors

julia> A = rand(RGB, 10, 10) # 3つのカラー チャンネル
10×10 Array{RGB{Float64},2}:
[...]

julia> augment(A, ConvertEltype(Gray{Float32})) # グレースケールに変換
10×10 Array{Gray{Float32},2}:
[...]
```
