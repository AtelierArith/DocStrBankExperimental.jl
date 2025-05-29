```
bootstrapCL!(CH::ControlChart[; rlsim::Function, kw...])
```

制御チャートの名目特性を満たす制御限界を計算します。ブートストラップされたパスに対して二分法アルゴリズムを使用します（例として Qiu, 2013 を参照）。

### 引数

  * `CH` - 制御チャート。

### キーワード引数

  * `rlsim` - 制御チャート統計のパスを生成する関数で、シグネチャは `rlsim(CH; maxiter)` です。指定しない場合は、デフォルトで `run_path_sim` になります。関数のシグネチャに関する詳細は `run_path_sim` のヘルプを参照してください。
  * `settings` - アルゴリズムの動作を制御する変数を含む `OptSettings` オブジェクト。アルゴリズムの動作を制御する設定に関する情報は、以下の `Accepted settings` セクションを参照してください。各キーワード引数の具体的な詳細については、例として Qiu (2013) を参照してください。
  * `maxiter` - 二分法の最大反復回数。
  * `nsims` - 目標名目特性を推定するために使用されるラン長の数。
  * `maxrl` - ラン長が切り捨てられる最大ラン長で、過剰な計算を避けるためのものです。
  * `x_tol` - アルゴリズムの絶対許容誤差で、$h^{(k+1)} - h^{(k)} < x_{\text{tol}}$ の場合に終了します。
  * `f_tol` - アルゴリズムの絶対許容誤差で、$\text{target}(h^{(k+1)}) - \text{target}(h^{(k)}) < f_{\text{tol}}$ の場合に終了します。

### 戻り値

  * 推定された制御限界 `h`、総反復回数 `iter`、およびアルゴリズムの収束に関する情報 `status` を含む `NamedTuple`。

### 参考文献

  * Qiu, P. (2013). Introduction to Statistical Process Control. Boca Raton: CRC Press.
