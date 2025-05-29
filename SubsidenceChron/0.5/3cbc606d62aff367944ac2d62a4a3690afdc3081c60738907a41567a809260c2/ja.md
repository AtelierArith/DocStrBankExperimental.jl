```julia
SubsidenceStratMetropolis(smpl::ChronAgeData, config::StratAgeModelConfiguration, therm::ThermalSubsidenceParameters, subsidence_strat_depths, Sμ, Sσ, beta_ip, t0_ip;
    subsidencebotom=minimum(smpl.Height),
    subsidencetop=maximum(smpl.Height),
    lithosphere = Normal(125000, 100),
)
```

指定されたガウス年齢制約のセット、`smpl`構造体で指定された年齢-深度モデル構成、`therm`構造体で定義された熱沈下パラメータ、`subsidence_strat_depths`、`Sμ`、および`Sσ`の形での脱圧およびバックストリッピング出力、伸張係数ベータの事前推定（`beta_ip`）および熱沈下開始時刻（`t0_ip`）を与えて、メインのSubsidenceChron.jl年齢-深度モデルルーチンを実行します。

### 例:

```julia
(subsmdl, agedist, lldist, beta_t0dist, lldist_burnin) = SubsidenceStratMetropolis(smpl, config, therm, subsidence_strat_depths, Sμ, Sσ_corr, Beta_sigma/10, T0_sigma/10)
```
