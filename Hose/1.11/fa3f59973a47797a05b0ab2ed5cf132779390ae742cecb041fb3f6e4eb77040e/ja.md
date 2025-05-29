```julia
    @hose(expression)
```

`@hose` マクロは、その引数を処理して、左辺（LHS）を複数の引数を持つ関数、マクロ、ブロックにパイプしたり、LHSをインデックスしたりします。右辺のプレースホルダーシンボルはアンダースコア（`_`）です。

例:

```julia
    @hose a |> b(x, _) # b(x, a) を生成します
    @hose a |> _[b] # a[b] を生成します
    @hose a |> @testmacro _ b # @testmacro(a, b) と同等です
```

また、[Lazy.jl](https://github.com/MikeInnes/Lazy.jl) の `@>` マクロのように動作します:

```julia
    @hose a |> b(x) # b(a, x) を生成します
    @hose a |> @testmacro # @testmacro(a) と同等のものを生成します
```

標準のパイピングも機能します。他の例については `test/runtests.jl` を参照してください。
