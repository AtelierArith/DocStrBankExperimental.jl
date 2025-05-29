```
    solve(starting_state::Vector{Int64}; verbose=false, max_solutions=1, deterministic=false) :: Bool
        starting_state      `提供された制約行列（グローバル `incidence_matrix`）へのインデックスによる行のリストで、削除すべき行 - それらは解の一部として「与えられた」ものです。`
        [verbose]           `グローバル `VERBOSE` フラグを設定します; 時間を印刷します。`
        [max_solutions]     `グローバル `SOLUTIONSMAX` を設定します; 戻る前に見つけるべき解の数。`
        [deterministic]     `グローバル `DO_DETERMINISTICALLY` を設定します; false=ランダムに行を選択します。`
```

制約行列、グローバル `incidence_matrix` を解決します。

解が見つかったかどうかを返します。

最初に `exact_cover()` 関数でグローバル `incidence_matrix` を設定しておく必要があります。
