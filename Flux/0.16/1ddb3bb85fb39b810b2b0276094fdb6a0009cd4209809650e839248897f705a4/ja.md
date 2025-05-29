```
ConvTranspose(filter, in => out, σ=identity; stride=1, pad=0, outpad=0, dilation=1, [bias, init])
ConvTranspose(weight, [bias, activation; stride, pad, outpad, dilation])
```

標準的な畳み込み転置層です。`filter`は畳み込みカーネルのサイズを指定する整数のタプルであり、`in`と`out`は入力チャネルと出力チャネルの数を指定します。

ここで`pad=SamePad()`は、`size(output,d) == size(x,d) * stride`を確保しようとします。

`stride > 1`のときに[`Conv`](@ref)の逆可逆性を保つために、`outpad`を使用して出力のサイズを希望の次元で増加させることができます。`pad`は入力をゼロパディングするために使用され、`outpad`は出力の形状にのみ影響します。

パラメータは追加のキーワードによって制御され、デフォルトは`init=glorot_uniform`および`bias=true`です。

コンストラクタの2番目の形式では、事前に構築された重み行列とバイアスベクトルを渡すことができます。これは、重みを自分で初期化したい場合に便利です。

キーワードの詳細な説明については、[`Conv`](@ref)も参照してください。

# 例

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50);  # 50枚のRGB画像のバッチ

julia> layer = ConvTranspose((5,5), 3 => 7, relu)
ConvTranspose((5, 5), 3 => 7, relu)  # 532パラメータ

julia> layer(xs) |> size
(104, 104, 7, 50)

julia> ConvTranspose((5,5), 3 => 7, stride=2)(xs) |> size
(203, 203, 7, 50)

julia> ConvTranspose((5,5), 3 => 7, stride=2, outpad=1)(xs) |> size
(204, 204, 7, 50)

julia> ConvTranspose((5,5), 3 => 7, stride=3, pad=SamePad())(xs) |> size
(300, 300, 7, 50)
```

```jldoctest
julia> weight = rand(Float32, 3, 4, 5);

julia> bias = zeros(Float32, 4);

julia> layer = ConvTranspose(weight, bias, sigmoid)
ConvTranspose((3,), 5 => 4, σ)  # 64パラメータ

julia> layer(randn(Float32, 100, 5, 64)) |> size  # 転置畳み込みは次元サイズを増加させます（アップサンプリング）
(102, 4, 64)

julia> Flux.trainables(layer) |> length
2
```
