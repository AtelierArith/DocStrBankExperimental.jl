```
COLNEW(; bvpclass = 1, collocationpts = 7, diagnostic_output = 1,
    max_num_subintervals = 3000, bc_func = nothing, dbc_func = nothing,
    zeta = nothing)
COLNEW(bvpclass::Int, collocationpts::Int, diagnostic_output::Int,
    max_num_subintervals::Int, bc_func, dbc_func, zeta::AbstractVector)
```

## キーワード引数:

  * `bvpclass`: 境界値問題の分類、デフォルトは非線形で「特に敏感」、利用可能な選択肢:

      * `0`: 線形境界値問題。
      * `1`: 非線形で通常。
      * `2`: 非線形で「特に敏感」（最初の緩和係数はrstartであり、非線形反復は過去の収束に依存しない）。
      * `3`: 早期失敗: a) 2回連続して収束しない場合に即座に返す。 b) 最初のエラー推定を取得した後。
  * `collocationpts`: 各サブ区間のコレクションポイントの数。orders[i] ≤ k ≤ 7が必要で、デフォルトは7。
  * `diagnostic_output`: COLNEWの診断出力、デフォルトは出力なし、利用可能な選択肢:

      * `-1`: 完全な診断出力。
      * `0`: 選択された出力。
      * `1`: 出力なし。
  * `max_num_subintervals`: 最大サブ区間の数、デフォルトは3000。
  * `bc_func`: ODEInterface.jlに従った境界条件、マルチポイントBVPのみに使用。
  * `dbc_func`: ODEInterface.jlに従った境界条件のヤコビアン、マルチポイントBVPのみに使用。
  * `zeta`: 境界条件が指定される区間のポイント、マルチポイントBVPのみに使用。

Fortran77コードは、混合次数のODEシステムのためのマルチポイント境界値問題を解決します。bスプラインを置き換える新しい基底表現を取り入れ、線形および非線形代数方程式ソルバーの改善を行っています。

!!! 警告     2点境界値問題のみをサポートします。

!!! 注     `ODEInterface`パッケージがロードされている場合のみ利用可能です。
