```
Bilinear((in1, in2) => out, σ=identity; bias=true, init=glorot_uniform)
Bilinear(W::AbstractArray, [bias, σ])
```

2つの入力と出力の間で完全に接続されたレイヤーを作成し、その他は[`Dense`](@ref)に似ています。ベクトル`x`と`y`が与えられた場合、その出力は別のベクトル`z`であり、すべての`i ∈ 1:out`について次のようになります。

```
z[i] = σ(x' * W[i,:,:] * y + bias[i])
```

`x`と`y`が行列の場合、出力`z = B(x, y)`の各列はこの形式になります。ここで、`B`はBilinearレイヤーです。

2番目の入力`y`が指定されていない場合、それは`x`と等しいと見なされます。すなわち、`B(x) == B(x, x)`です。

2つの入力はタプルとして提供することもでき、`B((x, y)) == B(x, y)`となり、`Chain`への入力として受け入れられます。

2つの入力サイズが同じ場合、`in1 == in2`であれば、`Bilinear(in => out, σ)`と記述できます。

初期化は[`Dense`](@ref)レイヤーと同様に機能し、`W = init(out, in1, in2)`となります。デフォルトではバイアスベクトルは`zeros(Float32, out)`であり、オプション`bias=false`は学習可能なバイアスをオフにします。これらのいずれかを明示的に提供することもできます。

# 例

```jldoctest
julia> x, y = randn(Float32, 5, 32), randn(Float32, 5, 32);

julia> B = Flux.Bilinear((5, 5) => 7)
Bilinear(5 => 7)    # 182パラメータ

julia> B(x) |> size  # 1つの入力に基づく相互作用
(7, 32)

julia> B(x,y) == B((x,y))  # 2つの入力、タプルとして与えることができる
true

julia> sc = SkipConnection(
                Chain(Dense(5 => 20, tanh), Dense(20 => 9, tanh)),
                Flux.Bilinear((9, 5) => 3, bias=false),
            );  # 再結合器として使用され、スキップが2番目の入力

julia> sc(x) |> size
(3, 32)

julia> Flux.Bilinear(rand(4,8,16), false, tanh)  # 重みの最初の次元は出力
Bilinear((8, 16) => 4, tanh; bias=false)  # 512パラメータ
```
