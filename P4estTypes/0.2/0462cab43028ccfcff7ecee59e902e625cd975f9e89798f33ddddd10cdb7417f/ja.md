```
refine!(forest; refine = (_...) -> false, kw...)
```

`refine` コールバックによって決定されたフォレストの四分木を洗練します。`refine(forest, treeid, quadrant)` コールバックは、ランクにローカルな各四分木に対して呼び出されます。コールバックが `true` を返すと、`quadrant` は複数の四分木に洗練され、それ以外の場合は変更されません。

洗練のための他のキーワード引数 (`kw...`) は次の通りです：

  * `recursive`: `true` の場合、洗練は再帰的に行われ、それ以外の場合は各ランクローカルの四分木は一度だけ訪問されます。
  * `maxlevel = -1`: この呼び出し中に可能な最大の洗練レベル。
  * `init = nothing`: 各作成された四分木のユーザーデータを初期化するために呼び出されるプロトタイプ `init(forest, treeid, quadrant)` のコールバック関数。
  * `replace = nothing`: 各 `outgoing` 四分木とその関連する `incoming` 四分木に対して呼び出されるプロトタイプ `replace(forest, treeid, outgoing, incoming)` のコールバック関数。`outgoing` と `incoming` はどちらも `eltype` [`QuadrantWrapper`](@ref) の配列です。

詳細については、`@doc P4estTypes.P4est.p4est_refine_ext` および `@doc P4estTypes.P4est.p8est_refine_ext` を参照してください。
