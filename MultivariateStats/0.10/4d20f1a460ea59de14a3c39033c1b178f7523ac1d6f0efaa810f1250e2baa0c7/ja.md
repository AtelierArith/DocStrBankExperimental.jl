```
fit(MetricMDS, X; kwargs...)
```

`X`ポイントの埋め込みを（非）計量多次元尺度法（MDS）によって計算します。

**キーワード引数:**

`(d, n) = size(X)`をそれぞれ入力次元と観測数とします：

  * `distances`: 入力の選択（*必須*）:

      * `false`: ユークリッド距離を使用して不似合い行列を計算するために`X`を使用
      * `true`: 事前に計算された不似合い対称行列（距離）として`X`入力を使用
  * `maxoutdim`: 最大出力次元（*デフォルト* `d-1`）
  * `metric` : 不均衡値の計算のための関数

      * `nothing`: 計量MDSを実行するために不似合い値を不均衡として使用（*デフォルト*）
      * `isotonic`: 不似合い値を順序不均衡に変換して非計量MDSを実行
      * 最初のパラメータが近接性（すなわち不似合い）ベクトルで、2番目のパラメータが距離ベクトルである任意の2パラメータ不均衡変換関数、例えば`(p,d)->b*p`は*比率*MDSの変換関数です。
  * `tol`: 収束許容値（*デフォルト* `1.0e-3`）
  * `maxiter`: 最大反復回数（*デフォルト* `300`）
  * `initial`: 初期の縮小空間ポイント構成

      * `nothing`: その場合、初期構成はランダムに生成されます（*デフォルト*）
      * 事前定義された行列
  * `weights`: 重み行列

      * `nothing`: その場合、重みは1に設定されます、$w_{ij} = 1$（*デフォルト*）
      * 事前定義された行列

*注意:* アルゴリズムが収束できない場合、`ConvergenceException`がスローされます。
