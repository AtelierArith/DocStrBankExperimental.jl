メトロポリス調整ラプラスアルゴリズム（MALA）による自動ステップサイズ選択。

簡単に言うと、各イテレーションで、受け入れ率が合理的な範囲にあるまで、ステップサイズが指数関数的に縮小または拡大されます。可逆性チェックにより、移動がターゲットに対して可逆であることが保証されます。このプロセスは`step_size`から始まり、各ラウンドの終わりにすべてのチェーンで使用された平均指数に設定されます。

探索ごとのステップ数は`base_n_refresh * ceil(Int, dim^exponent_n_refresh)`に設定されます。

各ラウンドで、経験的な対角マージナル標準偏差行列が推定されます。各ステップで、アイデンティティと推定された標準偏差の間のランダムな補間が問題を条件付けるために使用されます。

通常の状況では調整の必要はありませんが、以下のオプションのキーワードパラメータが利用可能です：

  * `base_n_refresh`: スワップ間のステップ数（同等に、モメンタムリフレッシュ）の基数。この基数は`ceil(Int, dim^(exponent_n_refresh))`で乗算されます。
  * `exponent_n_refresh`: 次元性に応じたリフレッシュメントの数の増加をスケールするために使用されます。
  * `default_autodiff_backend`: 自動微分に使用するデフォルトのバックエンド。詳細は https://github.com/tpapp/LogDensityProblemsAD.jl#backends を参照してください。

    特定のターゲットはこれを無視する場合があります。たとえば、手動微分が提供されている場合や、Stanなどの外部プログラムを呼び出す場合です。
  * `step_size`: 自動ステップサイズアルゴリズムの開始点。各ラウンドの間に自動的に更新されます。
  * `preconditioner`: プレコンディショナーを構築するための戦略。
  * `estimated_target_std_deviations`: 最初のイテレーション後に更新されます。初期状態は`nothing`で、その場合はアイデンティティ質量行列が使用されます。

参考文献: Biron-Lattes, M., Surjanovic, N., Syed, S., Campbell, T., & Bouchard-Côté, A.. (2024).  [autoMALA: Locally adaptive Metropolis-adjusted Langevin algorithm](https://proceedings.mlr.press/v238/biron-lattes24a.html).  *Proceedings of The 27th International Conference on Artificial Intelligence and Statistics*,  in *Proceedings of Machine Learning Research* 238:4600-4608.
