```
    exact_cover(matrix::Matrix{Bool}; do_check::Bool)
        matrix      `インシデンス行列`
        do_check    `無効な行または列をチェックするかどうか。
                    （これにより実行時間が遅くなります。）`
```

グローバル変数 `incidence_matrix`、`nrows`、`ncols` を初期化します。
