```julia
TransitionRateMatrix(Q)

```

引数から遷移率行列を作成します。これによりコピーが作成され、対角外の要素が非負であることが確認され、行の合計が `0` になるように対角が設定され、スパース性と構造を保つように努めます。
