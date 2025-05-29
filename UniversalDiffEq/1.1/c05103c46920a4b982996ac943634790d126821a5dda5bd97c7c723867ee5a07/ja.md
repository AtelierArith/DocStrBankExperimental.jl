```
CustomDerivatives(data::DataFrame,derivs!::Function,initial_parameters,priors::Function;kwargs ... )
```

関数の priors が提供されると、その値はユーザー指定のパラメータに対するペナルティ項として損失関数に追加されます。これは、単一の NamedTuple `p` を引数として受け取り、各パラメータのペナルティは `p` にドット演算子でアクセスすることで計算されるべきです。

prior 関数は、パラメータ値に対する事前の期待に向けてフィッティングされたモデルを調整するために使用できます。例えば、以下の関数は、パラメータ `p.r` の値が 1.5 以外のときに損失を増加させ、2 番目のパラメータ `p.beta` がゼロより大きい場合に損失を増加させます。

```julia
function priors(p)
    l = 0.01*(p.r - 1.5)^2
    l += 0.01*(p.beta)^2
    return l
end
```

# kwargs

  * `time_column_name`: `data` の中で時間に対応する列の名前。デフォルトは `"time"`。
  * `proc_weight`: プロセス誤差 $omega_{proc}$ の重み。デフォルトは `1.0`。
  * `obs_weight`: 観測誤差 $omega_{obs}$ の重み。デフォルトは `1.0`。
  * `reg_weight`: 正則化誤差 $omega_{reg}$ の重み。デフォルトは `10^-6`。
  * `reg_type`: 正則化のタイプ、`"L1"` または `"L2"` 正則化のいずれか。デフォルトは `"L2"`。
  * `l`: 予測のための外挿パラメータ。デフォルトは `0.25`。
  * `extrap_rho`: 予測のための外挿パラメータ。デフォルトは `0.0`。
  * `ode_solver`: 微分方程式の解を近似するためのメソッド。デフォルトは `Tsit5()`。
  * `ad_method`: ODE ソルバーの導関数を評価するためのメソッド。デフォルトは `ForwardDiffSensitivity()`。
