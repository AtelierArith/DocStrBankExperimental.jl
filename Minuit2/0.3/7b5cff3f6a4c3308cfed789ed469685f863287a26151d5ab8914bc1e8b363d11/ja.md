```
Minuit 構造
```

## 直接または計算されたフィールド

  * `funcname::String` : 関数の名前
  * `x0::AbstractVector` : 初期パラメータ値
  * `method::Symbol` : 使用する最小化アルゴリズム。可能な値は `:migrad`, `:simplex`
  * `tolerance::Real` : 最小化のための許容誤差。0に設定すると、Minuitはデフォルト値を使用します。
  * `precision::Union{Real,Nothing}` : 最小化のための精度
  * `strategy::Int` : 最小化のための戦略 (0,1(デフォルト),2)。詳細はマニュアルを参照してください。
  * `values` : 最小値でのパラメータの値
  * `errors` : 最小値でのパラメータの誤差
  * `fixed` : パラメータの固定状態
  * `limits` : パラメータの制限
  * `is_valid` : 最小化が成功したかどうか
  * `fval` : 最小値での関数の値
  * `edm` : 最小値までの推定距離
  * `nfcn` : 関数呼び出しの回数
  * `ngrad` : 勾配呼び出しの回数
  * `niter` : 反復の回数
  * `npars` : パラメータの数
  * `ndof` : 自由度の数
  * `covariance` : パラメータの共分散行列
  * `is_above_max_edm` : 推定距離が最大を超えているかどうか
  * `has_parameters_at_limit` : パラメータのいずれかが制限に達しているかどうか
  * `has_accurate_covar` : 共分散行列が正確であるかどうか
  * `has_posdef_covar` : 共分散行列が正定値であるかどうか
  * `has_made_posdef_covar` : 共分散行列が正定値にされたかどうか
  * `hesse_failed` : ヘッセアルゴリズムが失敗したかどうか
  * `has_covariance` : 共分散行列が利用可能かどうか
  * `covariance` : パラメータの共分散行列
  * `has_accurate_covar` : 共分散行列が正確であるかどうか
  * `has_valid_parameters` : パラメータが有効であるかどうか
  * `has_reached_call_limit` : 最大関数呼び出し回数に達したかどうか
  * `minos` : Minos誤差
  * `parameters` : パラメータの値と誤差
