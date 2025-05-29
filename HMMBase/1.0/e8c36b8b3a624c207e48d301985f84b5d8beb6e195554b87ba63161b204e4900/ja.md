```
fit_mle(hmm, observations; ...) -> AbstractHMM
```

EM（Baum-Welch）アルゴリズムを使用してHMMパラメータを推定します。`hmm`は初期状態として使用されます。

**キーワード引数**

  * `display::Symbol = :none`: 収束ログを表示するタイミング。`:iter`または`:final`に設定できます。
  * `init::Symbol = :none`: `:kmeans`に設定すると、HMMパラメータはK-meansクラスタリングを使用して初期化されます。
  * `maxiter::Integer = 100`: 実行する最大反復回数。
  * `tol::Integer = 1e-3`: 対数尤度の改善が`tol`未満になった場合、アルゴリズムを停止します。

**出力**

  * `<:AbstractHMM`: 更新されたパラメータを持つ元のHMMのコピー。
