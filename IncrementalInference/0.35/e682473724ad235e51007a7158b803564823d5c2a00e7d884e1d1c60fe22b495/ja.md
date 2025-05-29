```julia
factorCanInitFromOtherVars(dfg, fct, loovar; solveKey)

```

`(::Bool, ::OKVarlist, ::NotOkayVarList)`を返します。これは、因子`fct::Symbol`に付随する他のすべての変数（`loovar::Symbol`を除く）が初期化されているかどうか、つまり`fct`が使用可能であるかどうかを示します。

ノート：

  * 特別な取り決めとして、少なくとも1つの仮説が利用可能であるべきですが、最初にすべての必要なものが揃っている必要はない多仮説ケースについては、問題427を参照してください。

開発ノート

  * TODO データベースバージョンのためのisInitializedのより高速なバージョンを取得する

関連

doautoinit!, initVariable!, isInitialized, isMultihypo
