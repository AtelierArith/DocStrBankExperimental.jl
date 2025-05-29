```
last_quote_currency_pair(opts::PolyOpts, from="AUD", to="USD")
```

外国為替通貨ペアの最新のクオートティックを取得します。

# 引数

  * opts::PolyOpts: リクエストを構成するために使用されるPolyOptsオブジェクト。
  * from: ペアの「from」シンボル。
  * to: ペアの「to」シンボル。

# 例

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> last_quote_currency_pair(opts, "AUD", "USD")
```

# 戻り値

  * JSON3.ArrayまたはJSON3.Arrayの指定された表形式の表現
  * 応答属性およびサポートされているキーワード引数に関するドキュメントは、https://polygon.io/docs/get*v1*last*quote*currencies**from___to**anchor を参照してください。
