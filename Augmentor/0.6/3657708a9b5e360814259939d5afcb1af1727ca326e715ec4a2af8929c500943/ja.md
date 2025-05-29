```
Reshape <: Augmentor.Operation
```

## 説明

与えられた数値または色素の配列の形状を再解釈します。これは、例えば、深層学習フレームワークが無色画像に必要とするシングルトン次元を作成するためや、画像配列を特徴ベクトルに変換する（その逆も）ために便利です。

## 使用法

```
Reshape(dims)

Reshape(dims...)
```

## 引数

  * **`dims`** : 出力画像の各次元の新しいサイズ。`Vararg{Int}`または`Int`の`NTuple`として指定する必要があります。

## 参照

[`CombineChannels`](@ref), [`augment`](@ref)

## 例

```julia-repl
julia> using Augmentor, Colors

julia> A = rand(10,10)
10×10 Array{Float64,2}:
[...]

julia> augment(A, Reshape(10,10,1)) # トレーリングシングルトン次元を追加
10×10×1 Array{Float64,3}:
[...]
```
