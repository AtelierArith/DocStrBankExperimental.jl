```
CrossCor(filter, in => out, σ=identity; stride=1, pad=0, dilation=1, [bias, init])
CrossCor(weight::AbstractArray, [bias, activation; stride, pad, dilation])
```

標準的なクロスコリレーション層です。`filter`は畳み込みカーネルのサイズを指定する整数のタプルであり、`in`と`out`は入力チャネルと出力チャネルの数を指定します。

パラメータは追加のキーワードによって制御され、デフォルトは`init=glorot_uniform`および`bias=true`です。

コンストラクタの2番目の形式では、事前に構築された重み行列とバイアスベクトルを渡すことができます。これは、重みを自分で初期化したい場合に便利です。

キーワードの詳細な説明については、[`Conv`](@ref)も参照してください。

# 例

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);  # 50枚のRGB画像のバッチ

julia> layer = CrossCor((5,5), 3 => 6, relu; bias=false)
CrossCor((5, 5), 3 => 6, relu, bias=false)  # 450パラメータ

julia> layer(xs) |> size
(96, 96, 6, 50)

julia> CrossCor((5,5), 3 => 7, stride=3, pad=(2,0))(xs) |> size
(34, 32, 7, 50)
```

```jldoctest
julia> weight = rand(Float32, 3, 4, 5);

julia> bias = zeros(Float32, 5);

julia> layer = CrossCor(weight, bias, relu)
CrossCor((3,), 4 => 5, relu)  # 65パラメータ

julia> layer(randn(Float32, 100, 4, 64)) |> size
(98, 5, 64)
```
