```julia
columns(ft)

```

`NamedTuple`で列を返します。

各列は反復可能ですが、必ずしも`<: AbstractVector`ではありません。

!!! note
    **このメソッドで取得した列を決して変更しないでください**。そうしないと、実装によって仮定された不変条件が破られます。可変ベクトルを取得するには、`map(collect, columns(ft))`やそれに類似したものを使用してください。

