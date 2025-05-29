```
loadSPAC(folder::String, prefix::String;
        # OPTIONAL ARGUMENTS ARE:
        simulate_isotopes::Bool = true,
        canopy_evolution  = "meteoveg.csv",
        Δz_thickness_m    = "soil_discretization.csv",
        root_distribution = "soil_discretization.csv",
        IC_soil           = "soil_discretization.csv",
        IC_scalar         = "initial_conditions.csv",
        storm_durations_h = "meteo_storm_durations.csv")
```

SPACモデルのインスタンスを作成するには、フォルダー`folder`から異なる入力ファイルを読み込み、次の名前を付けます：

  * `[PREFIX]_meteoveg.csv`
  * `[PREFIX]_meteo_iso.csv`（同位体に必要）
  * `[PREFIX]_param.csv`
  * `[PREFIX]_meteo_storm_durations.csv`
  * `[PREFIX]_initial_conditions.csv`
  * `[PREFIX]_soil_horizons.csv`

これらのファイルは、R関数`LWFBrook90R::run_LWFB90()`と同じ引数を取るRスクリプト`generate_LWFBrook90jl_Input.R`を使用して作成され、LWFBrook90.jl用の対応する入力ファイルを生成します。

土壌の離散化は、各セルの厚さのベクトルとして提供できます。例：`Δz_thickness_m = fill(0.04, 20)`。

根の分布は、関数`Rootden_()`への引数として提供できます。例：（`(beta = 0.98, )`）または（`(beta = 0.98, z_rootMax_m=-0.5)`）またはガンマ分布の場合（`(root_k = 1.0, root_θ_cm = 20.0, z_rootMax_m=-0.5)`）。

気象の嵐の持続時間は、各月のベクトルとして提供できます。例：`[4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4]`

土壌の初期条件は、NamedTupleとして提供できます。例：`IC_soil = (PSIM_init_kPa = -7.0, delta18O_init_permil = -9.0, delta2H_init_permil = -11.0)`

キャノピーの進化は、NamedTupleとして提供でき、DENSEF、HEIGHT、SAIの定数値とLAIの動的進化を示します：

```
canopy_evolution = (DENSEF_rel = 100,
                    HEIGHT_rel = 100,
                    SAI_rel    = 100,
                    LAI_rel = (DOY_Bstart = 120,
                            Bduration  = 21,
                            DOY_Cstart = 270,
                            Cduration  = 60,
                            LAI_perc_BtoC = 100,
                            LAI_perc_CtoB = 20))
```

LAIの観点からの植生シーズンは、年を4つの部分に分けることで定義されます：A->B、B->B+、B+->C、C->C+、C+->A、ここでAは年の始まり（1月1日）です。実際には、4つの部分：C+->B、B->B+、B+->C、C->C+が与えられます。これらの期間の位置と持続時間は、パラメータ：DOY*Bstart、Bduration、DOY*Cstart、およびCdurationによって日数で定義されます。LAI（パーセント）は、C+->BおよびB+->Cの間で一定です（LAI*perc*CtoBおよびLAI*perc*BtoCによって与えられます）および単純な線形補間が行われます（すなわち、芽吹きと落葉の間）。

土壌以外の状態の初期条件は、NamedTupleとして提供できます。例：

```
IC_scalar = (amount = (u_GWAT_init_mm = 0,
                       u_INTS_init_mm = 0,
                       u_INTR_init_mm = 0,
                       u_SNOW_init_mm = 0,
                       u_CC_init_MJ_per_m2 = 0,
                       u_SNOWLQ_init_mm =  0),
            d18O    = (u_GWAT_init_permil = -13.,
                       u_INTS_init_permil = -13.,
                       u_INTR_init_permil = -13.,
                       u_SNOW_init_permil = -13.),
            d2H     = (u_GWAT_init_permil = -95.,
                       u_INTS_init_permil = -95.,
                       u_INTR_init_permil = -95.,
                       u_SNOW_init_permil = -95.))
```
