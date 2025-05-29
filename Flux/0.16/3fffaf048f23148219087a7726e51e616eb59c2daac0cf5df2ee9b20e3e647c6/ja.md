```
gradient(f, args::Union{Const,Duplicated}...)
```

これは `gradient(f, args...)` と同じ答えを返すはずですが、導関数を計算するために Zygote.jl の代わりに Enzyme.jl を使用します。

Enzyme がロードされているときのみ利用可能です！

このメソッドは、少なくとも1つの引数が `Duplicated` 型であり、すべての未指定の引数が `Const` でラップされているときに使用されます。Enzyme の `Active` はサポートされていないことに注意してください。

勾配を返すだけでなく、これは `Duplicated` オブジェクト内にも保存されます。`Enzyme.Duplicated(model)` を呼び出すと、勾配のためのスペースが確保され、`gradient` を呼び出す際に使用する前にゼロに初期化されます。キーワード `zero=false` を使用すると、新しい勾配は既に保存されているものに追加されます。

!!! warning "実験的"
    このような Enzyme サポートは新しく、やや実験的です。このメソッドは Flux 0.15 で追加されました。


# 例

```
julia> using Flux

julia> model = Chain(Dense([3.0;;]));

julia> Flux.gradient(model, [1]) do m, x  # Zygote を使用して計算
         sum(abs2, m(x))
       end
((layers = ((weight = [6.0;;], bias = [6.0], σ = nothing),),), [18.0])

julia> using Enzyme

julia> dup_model = Duplicated(model);  # 勾配のためのスペースを確保

julia> Flux.gradient(dup_model, Const([1])) do m, x  # Enzyme、同じ結果を返す
         sum(abs2, m(x))
       end
((layers = ((weight = [6.0;;], bias = [6.0], σ = nothing),),), nothing)

julia> dup_model  # 同じ勾配が Duplicated 内にも保存されている
Duplicated(
  Chain(
    Dense(1 => 1),                      # 2 パラメータ
  ),
  # norm(∇) ≈ 8.49
)

julia> Flux.destructure((weight = [6.0;;], bias = [6.0]))[1] |> norm
8.48528137423857

julia> Flux.gradient(dup_model, [1]; zero=false) do m, x  # 暗黙の Const([1])、および勾配の蓄積
         sum(abs2, m(x))
       end
((layers = ((weight = [12.0;;], bias = [12.0], σ = nothing),),), nothing)
```
