```
state(x)
```

`Functors.children` に従って `x` と同じネスト構造を持つオブジェクトを返しますが、基本的なコンテナ（例えば、名前付きタプル、タプル、配列、辞書）のみで構成されています。

訓練可能な配列と訓練不可能な配列に加えて、状態には数値、シンボル、文字列、何もない値などの配列でないリーフノードが含まれます。最終的に状態に含まれるリーフタイプは将来的に増加する可能性があります。

このメソッドは、状態が簡単にシリアライズできる単純なデータ型のみを含むため、モデルの保存と読み込みに特に便利です。

状態は [`loadmodel!`](@ref) に渡してモデルを復元することができます。

# 例

## 状態を別のモデルにコピーする

```jldoctest
julia> m1 = Chain(Dense(1, 2, tanh; init=ones), Dense(2, 1; init=ones));

julia> s = Flux.state(m1)
(layers = ((weight = [1.0; 1.0;;], bias = [0.0, 0.0], σ = ()), (weight = [1.0 1.0], bias = [0.0], σ = ())),)

julia> m2 = Chain(Dense(1, 2, tanh), Dense(2, 1; bias=false));  # 重みはランダムな数値

julia> Flux.loadmodel!(m2, s);

julia> m2[1].weight   # 現在、m2の重みはm1と同じ
2×1 Matrix{Float32}:
 1.0
 1.0

julia> Flux.state(trainmode!(Dropout(0.2)))  # p と activity を含むが、RNG状態は含まれない
(p = 0.2, dims = (), active = true, rng = ())

julia> Flux.state(BatchNorm(1))  # 訓練不可能な配列 μ, σ² を含む
(λ = (), β = Float32[0.0], γ = Float32[1.0], μ = Float32[0.0], σ² = Float32[1.0], ϵ = 1.0f-5, momentum = 0.1f0, affine = true, track_stats = true, active = nothing, chs = 1)
```

## BSONを使って保存と読み込み

```julia-repl
julia> using BSON

julia> BSON.@save "checkpoint.bson" model_state = s

julia> Flux.loadmodel!(m2, BSON.load("checkpoint.bson")[:model_state])
```

## JLD2を使って保存と読み込み

```julia-repl
julia> using JLD2

julia> JLD2.jldsave("checkpoint.jld2", model_state = s)

julia> Flux.loadmodel!(m2, JLD2.load("checkpoint.jld2", "model_state"))
```
