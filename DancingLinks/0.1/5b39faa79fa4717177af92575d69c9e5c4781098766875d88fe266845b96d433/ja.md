```
    solve(; verbose=false, max_solutions=1, deterministic=false) :: Bool
        [verbose]         `グローバル `VERBOSE` フラグを設定します; タイミングなどを印刷します。`
        [max_solutions]   `グローバル `SOLUTIONSMAX` を設定します; 戻る前に見つける解の数。`
        [deterministic]   `グローバル `DO_DETERMINISTICALLY` を設定します; false=行をランダムに選択します。`
```

制約行列を解決し、グローバル `incidence_matrix` を使用します。与えられた値なしで解決します。

解が見つかったかどうかを返します。

これは、グローバル `incidence_matrix` に提供された行列が実際の行列である場合（つまり、`givens` がない場合）に便利です。
