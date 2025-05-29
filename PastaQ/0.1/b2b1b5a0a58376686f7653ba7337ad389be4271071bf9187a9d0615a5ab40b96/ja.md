```
tomography(train_data::AbstractMatrix, L::LPDO;
           optimizer::Optimizer,
           observer! = nothing,
           kwargs...)
```

変分モデル $L$ を使用して `train_data` にフィットさせる量子プロセストモグラフィーを実行します。 `train_data` のタイプに応じて、状態またはプロセスのトモグラフィーを実行します（データ形式については完全なトモグラフィーのドキュメントを参照してください）。

量子状態トモグラフィーの場合、基底のセットにおける射影測定の平均カルバック・ライブラー（KL）ダイバージェンスを最適化します：

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log P(x_k^{(b)})
$$

ここでコスト関数は次のように計算されます。

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log |\langle x_k|U_b|\psi(\theta)\rangle|^2
$$

入力MPS変分波動関数の場合、そして

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log \langle x_k|U_b \rho(\theta) U_b^\dagger|x_k\rangle
$$

入力LPDO変分密度演算子の場合です。ここで $U_b$ は、変分状態を測定基底 $b$ に回転させる深さ1のユニタリです。

量子プロセストモグラフィーの場合、プロセス確率分布のKLダイバージェンスを最適化します。

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log P(x_k^{(b)}|\xi)
$$

ここで $\xi$ はチャネルへの入力状態です。コスト関数は次のように計算されます。

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log |\langle x_k|U_b|\tilde\Phi(\theta)\rangle|^2
$$

入力MPO変分ユニタリ演算子の場合（適切なベクトル化の後にMPS $|\Phi\rangle$として扱われます）、そして

$$
C(\theta) = -\frac{1}{|D|}\sum_{k=1}^{|D|} \log \langle x|U_b \tilde\Lambda(\theta) U_b^\dagger|x\rangle
$$

入力LPDO変分チョイ行列の場合です。ここで、$\tilde\Phi$ と $\tilde\Lambda$ はそれぞれユニタリ演算子またはチョイ行列のチャネルへの入力状態 $|\xi\rangle$ への射影を指します。

キーワード引数：

  * `train_data`: 準備/（基底/結果）のペア： `("X+"=>"X"=>0, "Z-"=>"Y"=>1, "Y+"=>"Z"=>0, …)`。
  * `L`: 変分モデル（MPO/LPDO）。
  * `optimizer`: 確率最適化のためのオプティマイザオブジェクト（`Optimisers.jl` から）。
  * `observer!`: 提供されている場合、トレーニングメトリクスを追跡します（`Observers.jl` から）。
  * `batch_size`: 1回の勾配更新に使用されるサンプルの数。
  * `epochs`: トレーニングの反復回数。
  * `target`: 距離測定のためのターゲット量子状態/プロセス（例：フィデリティ）。
  * `test_data`: クロスバリデーションのためのデータ。
  * `observer_step = 1`: 観測者が測定を記録するために呼び出される頻度。
  * `outputlevel = 1`: トレーニング中に画面に表示される情報の量。
  * `outputpath`: 提供されている場合、メトリクスをファイルに保存します。
  * `savestate`: `true` の場合、変分状態をファイルに保存します。
  * `print_metrics = []`: トレーニング中にこれらのメトリクスを画面に表示します。
  * `earlystop`: `true` の場合、事前定義された早期停止関数を使用します。関数を `earlystop` として渡すこともでき、その場合、関数（各反復で評価される）が `true` を返すとトレーニングが停止します。
