```
withgradient(f, args::Union{Const,Duplicated}...)
```

これは `withgradient(f, model, args...)` と同じ答えを返すはずですが、導関数を計算するために Zygote.jl の代わりに Enzyme.jl を使用します。

Enzyme がロードされているときのみ利用可能です！

!!! warning "実験的"
    このような Enzyme サポートは新しく、やや実験的です。このメソッドは Flux 0.15 で追加されました。


# 例

```julia-repl
julia> using Flux, Enzyme

julia> model = Chain(Embedding([1.1 2.2 3.3]), Dense([4.4;;]), only);

julia> model(3)
14.52

julia> Flux.withgradient(m -> m(3), model)  # これは Zygote を使用します
(val = 14.52, grad = ((layers = ((weight = [0.0 0.0 4.4],), (weight = [3.3;;], bias = [1.0], σ = nothing), nothing),),))

julia> Flux.withgradient(m -> m(3), Duplicated(model))  # これは Enzyme を使用します
(val = 14.52, grad = ((layers = ((weight = [0.0 0.0 4.4],), (weight = [3.3;;], bias = [1.0], σ = nothing), nothing),),))
```

関数 `f` は Tuple または NamedTuple を返すことができ、損失が最初の要素となります。勾配は `grad = gradient(first∘f, args...)` ですが、返される値は `val = f(args...)` です：

```julia-repl
julia> Flux.withgradient(m -> (m(3), "aux"), Duplicated(model))
(val = (14.52, "aux"), grad = ((layers = ((weight = [0.0 0.0 4.4],), (weight = [3.3;;], bias = [1.0], σ = nothing), nothing),),))

julia> Flux.withgradient(m -> (loss=m(3), aux=round.(m.(1:3); digits=3)), Duplicated(model))
(val = (loss = 14.52, aux = [4.84, 9.68, 14.52]), grad = ((layers = ((weight = [0.0 0.0 4.4],), (weight = [3.3;;], bias = [1.0], σ = nothing), nothing),),))
```
