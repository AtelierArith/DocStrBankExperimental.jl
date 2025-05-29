```
softmax(x; dims = 1)
```

[Softmax](https://en.wikipedia.org/wiki/Softmax_function) は、入力配列 `x` を、指定された次元 `dims` に沿って合計が1になる確率分布に変換します。これは、次のように意味的に等価です：

```
softmax(x; dims = 1) = exp.(x) ./ sum(exp.(x), dims = dims)
```

数値的安定性を高めるための追加の操作が含まれています。

行列入力 `x` に対しては、デフォルトで (`dims = 1`) ベクトルのバッチとして扱い、各列は独立しています。キーワード `dims = 2` は、代わりに行を独立して扱います。

[`logsoftmax`](@ref) も参照してください。

# 例

```jldoctest; filter = r"[+-]?([0-9]*[.])?[0-9]+(f[+-]*[0-9])?"
julia> softmax([1, 2, 3])
3-element Vector{Float64}:
 0.09003057317038046
 0.24472847105479764
 0.6652409557748218

julia> softmax([1 2 3; 2 2 2])  # dims=1
2×3 Matrix{Float64}:
 0.268941  0.5  0.731059
 0.731059  0.5  0.268941

julia> softmax([1 2 3; 2 2 2]; dims=2)
2×3 Matrix{Float64}:
 0.0900306  0.244728  0.665241
 0.333333   0.333333  0.333333
```

Flux.jl と一緒に使用する場合、`softmax` は、活性化関数を受け入れる `Dense` のようなレイヤーに渡されてはなりません。活性化は結果に対してブロードキャストされ、個々の数値に適用されます。しかし、`softmax` は常に全体の列を見る必要があります。

```julia-repl
julia> using Flux

julia> x = randn(Float32, 4, 4, 3, 13);

julia> model = Chain(Conv((4, 4), 3 => 8, tanh), Flux.flatten, Dense(8 => 7), softmax);

julia> model(x) |> size
(7, 13)

julia> Dense(4 => 7, softmax)(x)
ERROR: `softmax(x)` called with a number, but it expects an array. 
```
