```
coarsen!(forest; coarsen = (_...) -> false, kw...)
```

`coarsen` コールバックによって決定されたフォレストの四分木を粗くします。`coarsen(forest, treeid, siblings)` コールバックは、粗くするのに適したランクにローカルな兄弟四分木の各セットに対して呼び出されます。コールバックが `true` を返すと、`siblings` は1つの四分木に粗くされ、それ以外の場合はそのままになります。

粗くするための他のキーワード引数 (`kw...`) は次のとおりです：

  * `recursive = false`: `true` の場合、粗くする処理は再帰的になります。それ以外の場合、各ランクローカルの兄弟セットは1回だけ訪問されます。
  * `init = nothing`: ユーザーデータを初期化するために作成された各四分木に対して呼び出されるプロトタイプ `init(forest, treeid, quadrant)` のコールバック関数。
  * `replace = nothing`: 関連する `incoming` 四分木を持つ各 `outgoing` 四分木のセットに対して呼び出されるプロトタイプ `replace(forest, treeid, outgoing, incoming)` のコールバック関数。注意：`outgoing` と `incoming` はどちらも `eltype` [`QuadrantWrapper`](@ref) の配列です。

詳細については、`@doc P4estTypes.P4est.p4est_coarsen_ext` および `@doc P4estTypes.P4est.p8est_coarsen_ext` を参照してください。
