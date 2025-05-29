```
CustomDifference(data::DataFrame,step,initial_parameters,priors::Function;kwargs ... )
```

関数のpriorsが提供されると、その値はユーザー指定のパラメータに対するペナルティ項として損失関数に追加されます。これは、単一のNamedTuple `p`を引数として受け取り、各パラメータのペナルティは、ピリオド演算子を使って`p`にアクセスすることで計算されるべきです。

```julia
function priors(p)
    l = 0.01*(p.r - 1.5)^2
    l += 0.01*(p.beta)^2
    return l
end
```

# kwargs

  * `time_column_name`: `data`内の時間に対応する列の名前。デフォルトは`"time"`です。
  * `proc_weight`: プロセス誤差の重み $omega_{proc}$。デフォルトは`1.0`です。
  * `obs_weight`: 観測誤差の重み $omega_{obs}$。デフォルトは`1.0`です。
  * `reg_weight`: 正則化誤差の重み $omega_{reg}$。デフォルトは`10^-6`です。
  * `reg_type`: 正則化のタイプ、`"L1"`または`"L2"`正則化のいずれか。デフォルトは`"L2"`です。
  * `l`: 予測のための外挿パラメータ。デフォルトは`0.25`です。
  * `extrap_rho`: 予測のための外挿パラメータ。デフォルトは`0.0`です。
