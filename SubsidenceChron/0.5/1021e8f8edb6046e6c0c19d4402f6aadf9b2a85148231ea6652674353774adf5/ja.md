```julia
SubsidenceStratMetropolis_Height(smpl::ChronAgeData, config::StratAgeModelConfiguration, therm::ThermalSubsidenceParameters, subsidence_strat_depths, Sμ, Sσ, beta_ip, t0_ip;
    subsidencetop=maximum(smpl.Height),
    lithosphere = Normal(125000, 100),
)
```

与えられた一連のガウス年齢制約を指定した `smpl` 構造体、`config` 構造体で指定された年齢-深度モデル構成、`therm` 構造体で定義された熱沈下パラメータ、`subsidence_strat_depths`、`Sμ`、および `Sσ` の形での脱圧およびバックストリッピング出力、伸張係数ベータの事前推定（`beta_ip`）および熱沈下開始時刻の事前推定（`t0_ip`）を使用して、メインの SubsidenceChron.jl 年齢-深度モデルルーチンを実行します。

### 例:

```julia
(subsmdl, agedist, lldist, beta_tsdist, lldist_burnin, zdist) = SubsidenceStratMetropolis_Height(smpl, config, therm, subsidence_strat_depths, Sμ, Sσ_corr, Beta_sigma/10, T0_sigma/10)
```
