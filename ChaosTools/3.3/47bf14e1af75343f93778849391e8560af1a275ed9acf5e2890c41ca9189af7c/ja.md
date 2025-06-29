```
predictability(ds::CoreDynamicalSystem; kwargs...) -> chaos_type, ν, C
```

`ds`が強いカオス、部分的に予測可能なカオス、または規則的な挙動を示すかどうかを、[^Wernecke2017]で説明されているWerneckeらの方法を使用して判断します。

挙動のタイプ、交差距離スケーリング係数`ν`、および相関係数`C`を返します。`ν`、`C`、および`chaos_type`の典型的な値は、[^Wernecke2017]の表2に示されています：

| `chaos_type` | `ν` | `C` |
| ------------:| ---:| ---:|
|        `:SC` |   0 |   0 |
|       `:PPC` |   0 |   1 |
|       `:REG` |   1 |   1 |

これらの条件のいずれにも該当しない場合、返り値は`:IND`（不確定）です。

## キーワード引数

  * `Ttr = 200`: 軌道からサンプリングする前にシステムを進化させるための追加の過渡時間。離散システムの場合は`Int`である必要があります。
  * `T_sample = 1e4`: サンプルを取得するためにシステムを進化させる時間。離散システムの場合は`Int`である必要があります。
  * `n_samples = 500`: 統計計算に使用するサンプルの数。
  * `λ_max = lyapunov(ds, 5000)`: リャプノフ予測時間を見つけるために使用する最大リャプノフ指数の値。0未満の場合、すぐに規則的な結果が返されます。
  * `d_tol = 1e-3`: リャプノフ予測時間を計算するために使用する許容距離。
  * `T_multiplier = 10`: リャプノフ予測時間から評価時間への乗数。
  * `T_max = Inf`: 軌道距離を評価する最大時間。内部で計算された評価時間が`T_max`より大きい場合は、代わりに`T_max`で停止します。 **これを手動で設定することを強く推奨します！**
  * `δ_range = 10.0 .^ (-9:-6)`: スケーリング`ν`を決定するために使用する初期条件の摂動距離の範囲。
  * `ν_threshold = C_threshold = 0.5`: スケーリング係数の閾値（閾値より小さいまたは大きい場合、0または1になります）。

## 説明

アルゴリズムは、システムの軌道から初期条件として使用するポイントをサンプリングします。これらの初期条件のそれぞれは、距離`δ`によってランダムに摂動され、元の初期条件と摂動された初期条件の両方の軌道が「評価時間`T`」まで進化します（その定義は以下に示されています）。

時間`T`における状態の平均（サンプルに対して）距離と相互相関係数が計算されます。これは、`δ`の範囲（`δ_range`で定義）に対して繰り返され、線形回帰を使用して距離と相互相関が`δ`に対してどのようにスケールするかを決定し、カオスタイプを特定します。

評価時間`T`は`T = T_multiplier*Tλ`として計算され、リャプノフ予測時間`Tλ = log(d_tol/δ)/λ_max`です。`λ_max`が小さい場合、例えばシステムが規則的な場合、この内部で計算された時間`T`は、ユーザーによって設定された小さい`T_max`で上書きされる可能性があります。

## パフォーマンスノート

連続システムの場合、積分器によって使用される`maxiters`を増やす必要がある可能性があります。例えば、1e9に設定します。これは`diffeq`のキーワード引数の一部です。さらに、この関数は内部計算を*多く*行うことに注意してください。例えば、[`lyapunov`](@ref)とは異なる速度で動作しています。

[^Wernecke2017]: Wernecke, H., Sándor, B. & Gros, C. *部分的に予測可能なカオスをテストする方法*. [Scientific Reports **7**, (2017)](https://www.nature.com/articles/s41598-017-01083-x).

```
