```
Dense(in => out, σ=identity; bias=true, init=glorot_uniform)
Dense(W::AbstractMatrix, [bias, σ])
```

従来の完全接続層を作成し、その順伝播は次のように与えられます：

```
y = σ.(W * x .+ bias)
```

入力 `x` は長さ `in` のベクトル、または `in × N` 行列として表されるベクトルのバッチ、または `size(x,1) == in` である任意の配列である必要があります。出力 `y` は長さ `out` のベクトル、または `size(y) == (out, size(x)[2:end]...)` であるバッチになります。

キーワード `bias=false` は、層の学習可能なバイアスをオフにします。重み行列の初期化は `W = init(out, in)` で行われ、キーワード `init` に与えられた関数が呼び出され、デフォルトは [`glorot_uniform`](@ref Flux.glorot_uniform) です。重み行列および/またはバイアスベクトル（長さ `out`）も明示的に提供することができます。

# 例

```jldoctest
julia> model = Dense(5 => 2)
Dense(5 => 2)       # 12 パラメータ

julia> model(rand32(5, 64)) |> size
(2, 64)

julia> model(rand32(5, 6, 4, 64)) |> size  # 三つのバッチ次元として扱われる
(2, 6, 4, 64)

julia> model2 = Dense(ones(2, 5), false, tanh)  # 提供された重み行列を使用
Dense(5 => 2, tanh; bias=false)  # 10 パラメータ

julia> model2(ones(5))
2-element Vector{Float64}:
 0.9999092042625951
 0.9999092042625951

julia> Flux.trainables(model2)  # 学習可能なバイアスはなし
1-element Vector{AbstractArray}:
 [1.0 1.0 … 1.0 1.0; 1.0 1.0 … 1.0 1.0]
```
