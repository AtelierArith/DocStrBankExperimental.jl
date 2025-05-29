```
balance!(forest; kw...)
```

森林全体にわたって二対一の四分木サイズ制約を強制します。デフォルトでは、この制約は面、エッジ、およびコーナーにわたって強制されます。

バランシングのためのキーワード引数（`kw...`）は次のとおりです：

  * `connect`: 強制される制約のタイプで、次の値を取ることができます：

      * `P4estTypes.CONNECT_FULL(Val(4))`: 面とコーナーにわたって強制します。
      * `P4estTypes.CONNECT_FULL(Val(8))`: 面、エッジ、およびコーナーにわたって強制します。
      * `P4estTypes.CONNECT_FACE(Val(4))`: 面にわたって強制します。
      * `P4estTypes.CONNECT_FACE(Val(8))`: 面にわたって強制します。
      * `P4estTypes.CONNECT_EDGE(Val(8))`: 面とエッジにわたって強制します。
      * `P4estTypes.CONNECT_CORNER(Val(4))`: 面とコーナーにわたって強制します。
      * `P4estTypes.CONNECT_CORNER(Val(8))`: 面、エッジ、およびコーナーにわたって強制します。
  * `init = nothing`: ユーザーデータを初期化するために作成された各四分木に対して呼び出されるプロトタイプ `init(forest, treeid, quadrant)` のコールバック関数。
  * `replace = nothing`: 各 `outgoing` 四分木とその関連する `incoming` 四分木に対して呼び出されるプロトタイプ `replace(forest, treeid, outgoing, incoming)` のコールバック関数。`outgoing` と `incoming` はどちらも `eltype` [`QuadrantWrapper`](@ref) の配列です。

基礎となる p4est バランス関数に関する詳細については、`@doc P4estTypes.P4est.p4est_balance_ext` および `@doc P4estTypes.P4est.p8est_balance_ext` を参照してください。
