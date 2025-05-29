```
explain([io=stdout], match; context=40)
```

ドキュメント内で見つかったマッチとそのコンテキストの人間が読める説明を出力します。

## 例

```jldoctest
julia> document = Document("The crabeating macacue ate a crab.")
Document starting with "The crabeating macacue…". Metadata: NamedTuple()

julia> query = augment(FuzzyQuery("crab-eating macaque"))
Or
├─ FuzzyQuery("crab eating macaque", DamerauLevenshtein{Nothing}(nothing), 2)
├─ FuzzyQuery("crabeating macaque", DamerauLevenshtein{Nothing}(nothing), 2)
├─ FuzzyQuery("crab eatingmacaque", DamerauLevenshtein{Nothing}(nothing), 2)
└─ FuzzyQuery("crabeatingmacaque", DamerauLevenshtein{Nothing}(nothing), 2)

julia> m = match(query, document)
QueryMatch with distance 1 at indices 5:22.

julia> explain(m)
クエリ "crabeating macaque" はテキスト "The crabeating macacue ate a crab  " に距離 1 で一致しました。

julia> explain(m; context=5) # 出力されるコンテキストの量を調整
クエリ "crabeating macaque" はテキスト "The crabeating macacue ate…" に距離 1 で一致しました。

julia> sprint(explain, m) # 説明を文字列として取得
"The query \"crabeating macaque\" matched the text \"The crabeating macacue ate a crab  \" with distance 1.\n"

julia> explain(match(Query("crab"), document)) # 正確なクエリは少し異なる形式で出力される
クエリ "crab" はテキスト "The crabeating macacue ate a crab  " に正確に一致しました。

julia> explain(match(NamedQuery(Query("crab"), "crab query"), document)) # `NamedQuery` はその基になるクエリと同じように出力される
クエリ "crab" はテキスト "The crabeating macacue ate a crab  " に正確に一致しました。

```
