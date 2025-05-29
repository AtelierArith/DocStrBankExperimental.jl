```julia
calc_sigma_bound_test(state_errors, variances; dims, atol)

```

イノベーションの大きさの境界テスト (σ-bound-test)

状態値の約68%が⨦σ境界内にあるかどうかをテストします。パラメータdimsはモンテカルロ実行の次元または時間次元でなければなりません。
