KINSOL: ニュートン-クリロフ法ソルバー

```julia
KINSOL(;
    linear_solver = :Dense,
    jac_upper = 0,
    jac_lower = 0,
    userdata = nothing,
    prec_side = 0,
    krylov_dim = 0,
    globalization_strategy = :None
    maxsetupcalls=0
)
```

線形ソルバーの選択肢は次のとおりです：

  * `:Dense`: 密行列ソルバー
  * `:Band`: バンド行列ヤコビアンに特化したソルバー。使用する場合は、`jac_upper` と `jac_lower` を介して上部および下部の非ゼロ対角線の位置を設定する必要があります。
  * `:LapackDense`: Juliaが提供するOpenBLASリンクのLAPACKを使用した密行列ソルバーのバージョン。大規模なシステムでは `:Dense` よりも高速ですが、小規模なシステム（<100 ODE）では顕著なオーバーヘッドがあります。
  * `:LapackBand`: Juliaが提供するOpenBLASリンクのLAPACKを使用したバンド行列ソルバーのバージョン。大規模なシステムでは `:Band` よりも高速ですが、小規模なシステム（<100 ODE）では顕著なオーバーヘッドがあります。
  * `:GMRES`: GMRES法。推奨される最初の選択肢のクリロフ法。
  * `:BCG`: 双共役勾配法
  * `:PCG`: 前処理付き共役勾配法。対称線形システム専用。
  * `:TFQMR`: TFQMR法。
  * `:KLU`: スパース因子分解法。ユーザーがヤコビアンを指定する必要があります。ヤコビアンは `ODEProblem` 型でスパース行列として設定する必要があります。

グローバリゼーション戦略の選択肢は次のとおりです：

  * `:None`: グローバリゼーション戦略なし
  * `:LineSearch`: ラインサーチグローバリゼーション戦略

その他のオプション：

  * `maxsetupcalls`: 前処理器またはヤコビアンセットアップ関数への呼び出しの間に実行できる非線形反復の最大数。
