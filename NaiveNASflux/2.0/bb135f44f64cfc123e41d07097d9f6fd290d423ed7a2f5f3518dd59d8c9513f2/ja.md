```
LazyMutable
LazyMutable(m::AbstractMutableComp)
```

計算を実行するまで変異を行わないという意味でのMutableLayerの遅延バージョンです。

これにより、モデルを評価する前に複数の変異が頂点に適用される可能性がある場合に、ガーベジコレクションの必要性が減ります。

また、計算グラフの実際のレイヤーがグラフが使用されるまでインスタンス化されないようなファクトリーのような設計にも使用できます。

# 例

```jldoctest
julia> using NaiveNASflux, Flux

julia> struct DenseConfig end

julia> lazy = LazyMutable(DenseConfig(), 2, 3);

julia> layer(lazy)
DenseConfig()

julia> function NaiveNASflux.dispatch!(m::LazyMutable, ::DenseConfig, x)
       m.mutable = Dense(nin(m)[1], nout(m), relu)
       return m.mutable(x)
       end;

julia> lazy(ones(Float32, 2, 5)) |> size
(3, 5)

julia> layer(lazy)
Dense(2 => 3, relu)  # 9 parameters
```
