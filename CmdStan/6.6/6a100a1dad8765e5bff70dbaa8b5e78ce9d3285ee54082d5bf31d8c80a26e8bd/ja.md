# 変分型とコンストラクタ

Stanmodelにおけるmethod=Variational()の設定。

### メソッド

```julia
Variational(;
  grad_samples=1,
  elbo_samples=100,
  eta_adagrad=0.1,
  iter=10000,
  tol_rel_obj=0.01,
  eval_elbo=100,
  algorithm=:meanfield,          
  output_samples=10000
)
```

### オプション引数

```julia
* `algorithm::Symbol`             : 変分推論アルゴリズム
                                  : meanfield
                                  : fullrank
* `iter::Int64`                   : 最大反復回数
* `grad_samples::Int`             : 勾配のMC推定のためのサンプル数
* `elbo_samples::Int`             : ELBOのMC推定のためのサンプル数
* `eta::Float64`                  : 適応シーケンスのためのステップサイズ重み付けパラメータ
* `adapt::Adapt`                  : ウォームアップ適応
* `tol_rel_obj::Float64`          : 目的の相対ノルムに関する許容誤差
* `eval_elbo::Int`                : 目的の相対ノルムに関する許容誤差
* `output_samples::Int`           : 描画して保存する事後サンプルの数
```

### 関連ヘルプ

```julia
?Stanmodel                        : StanModelを作成する
?Stan.Method                      : 利用可能なトップレベルメソッド
?Stan.Adapt                       : 適応設定
```
