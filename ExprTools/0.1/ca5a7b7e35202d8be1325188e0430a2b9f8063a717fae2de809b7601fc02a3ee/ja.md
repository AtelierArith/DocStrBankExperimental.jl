```
combinedef(def::Dict{Symbol,Any}) -> Expr
```

さまざまなコンポーネントから関数定義式を作成します。通常、[`splitdef`](@ref) の結果を使用して関数を構築するために使用されます。

`def[:head]` が提供されていない場合、デフォルトで `:function` になります。

詳細については、[`splitdef`](@ref) に関するドキュメントを参照してください。
