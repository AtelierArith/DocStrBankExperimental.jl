```julia
calc_two_sigma_bound_test(
    state_errors,
    variances;
    dims,
    atol
)

```

イノベーションの大きさの境界テスト (2σ-bound-test)

状態値の約95%が⨦2σ境界内にあるかどうかをテストします。パラメータdimsはモンテカルロ実行の次元または時間次元でなければなりません。
