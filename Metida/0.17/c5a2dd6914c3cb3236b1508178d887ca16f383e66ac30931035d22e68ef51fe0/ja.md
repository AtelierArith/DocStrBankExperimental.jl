```
fit!(lmm::LMM{T}; kwargs...
) where T
```

LMMモデルをフィットします。

# キーワード:

  * `solver` - :default / :nlopt (MetidaNLopt.jlと使用するため) / :cuda (MetidaCu.jlと使用するため)
  * `verbose` - :auto / 1 / 2 / 3 - 1 - ログのみ, 2 - ログと印刷, 3 - エラーのみ印刷, その他のログ, 0 (または他の値) - ログなし
  * `varlinkf` - :exp / :sq / :identity [ref](@ref varlink_header)
  * `rholinkf` - :sigm / :atan / :sqsigm / :psigm
  * `aifirst` - AIのような方法での最初の反復 - :default / :ai / :score
  * `aifmax` - 最大事前最適化ステップ
  * `g_tol` - 勾配の絶対許容誤差
  * `x_tol` - シータベクトルの絶対許容誤差
  * `f_tol` - REMLの変化における絶対許容誤差
  * `hes` - REMLヘッセ行列を計算
  * `init` - 初期シータ値
  * `io` - 出力IO
  * `time_limit` - 時間制限 = 120秒
  * `iterations` - 最大反復回数 = 300
  * `refitinit` - true/false - `true`の場合 - 最後の値を初期条件に使用 (`false`がデフォルト)
  * `optmethod` - 最適化方法。Optim.jlのドキュメントを参照してください。(デフォルトはニュートン)
  * `singtol` - 特異許容誤差 = 1e-8
  * `maxthreads` - 最大スレッド = min(num_cores(), Threads.nthreads())
