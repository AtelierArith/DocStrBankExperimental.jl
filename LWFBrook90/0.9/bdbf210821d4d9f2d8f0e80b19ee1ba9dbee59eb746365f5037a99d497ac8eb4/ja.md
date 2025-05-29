```
remakeSPAC(discrSPAC::DiscretizedSPAC;
            requested_tspan = nothing,
            soil_output_depths_m::Vector = zeros(Float64, 0),
            kwargs...)
```

または

```
remakeSPAC(parametrizedSPAC::SPAC;
            requested_tspan = nothing,
            soil_output_depths_m::Vector = zeros(Float64, 0),
            kwargs...)
```

提供されたSPACまたはDiscretizedSPACのコピーを生成し、kwargsとして提供されたすべてのパラメータを修正します。これは、さまざまなパラメータで同じモデルを実行するのに便利です。

可能なkwargsは次のとおりです：

  * `soil_horizons = (ths_ = 0.4, Ksat_mmday = 3854.9, alpha_per_m = 7.11, gravel_volFrac = 0.1)`
  * `LAI_rel = (DOY_Bstart = 115,)`
  * `root_distribution = (beta = 0.88, z_rootMax_m = -0.6,)`
  * `params = (DRAIN=.33, BYPAR=1, IDEPTH_m=0.67, INFEXP=0.33,           ALB=0.15, ALBSN=0.7, RSSA=720., PSICR=-1.6, FXYLEM=0.4, MXKPL=16.5, MAXLAI=9.999,           GLMAX=.00801, R5=235., CVPD=1.9, CINTRL=0.18,)`
  * `IC_soil = (PSIM_init_kPa = -3.0, delta18O_init_permil = -15.55, )`
  * `IC_scalar = ICscalar_tochange`

引数`soil_horizons`にスカラー値が含まれている場合、トップレイヤーのパラメータはこの値に設定され、他のすべてのレイヤーのパラメータは比例的に修正されます。あるいは、引数`soil_horizons`には、各土壌層の値を持つベクトルまたはベクトルのセットを提供することもできます。ベクトルとスカラーの混合も可能です。
