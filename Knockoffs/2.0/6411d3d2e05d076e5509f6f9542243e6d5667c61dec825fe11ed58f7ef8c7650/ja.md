```
solve_group_max_entropy_hybrid(Σ, groups, [outer_iter=100], [inner_pca_iter=1],
    [inner_ccd_iter=1], [tol=0.0001], [ϵ=1e-6], [m=1], [robust=false], [verbose=false])
```

最大エントロピー目的に基づくグループノックオフ最適化問題を解決します。ユーザーはこの関数の代わりに `solve_s_group` を呼び出すべきです。

# 入力

  * `Σ`: 相関行列
  * `groups`: グループメンバーシップベクター

# オプション入力

  * `outer_iter`: 外部反復の最大数。各外部反復は `inner_pca_iter` PCA更新と `inner_ccd_iter` フル最適化更新を実行します（デフォルト = 100）。
  * `inner_pca_iter`: 完全なPCA更新の数、完全一般座標降下更新に変更する前（デフォルト = 1）
  * `inner_ccd_iter`: 完全一般座標降下更新の数、PCA更新に変更する前（デフォルト = 1）
  * `tol`: 収束許容値。アルゴリズムは `abs((obj_new-obj_old)/obj_old) < tol` または `S` 行列の変化が1e-4未満になると収束します。
  * `ϵ`: 下限および上限に追加される許容値、数値的問題を防ぎます（デフォルト = `1e-6`）
  * `m`: 変数ごとのノックオフの数（デフォルト `1`）
  * `robust`: "ロバスト" チョレスキー更新を使用するかどうか。`robust=true` の場合、アルゴリズムは約10倍遅くなります。`robust=false` がチョレスキー更新の失敗を引き起こす場合のみ使用してください。（デフォルト `false`）
  * `verbose`: 中間結果を表示するかどうか（デフォルト `false`）
