```julia
addFactor!(
    dfg,
    Xi,
    usrfnc;
    multihypo,
    nullhypo,
    solvable,
    tags,
    timestamp,
    graphinit,
    suppressChecks,
    inflation,
    namestring,
    _blockRecursion
)

```

ユーザー定義型`<:AbstractFactor`をファクターグラフオブジェクトに追加します。変数の自動初期化を行うべきかどうかを定義します。順序に敏感な`multihypo`キーワード引数を使用して、データ関連の不確実性に関連する変数があるかどうかを定義します。

実験的

  * `inflation`、畳み込み解決の前にカーネルをより良く分散させるために、IIF #1051を参照してください。
