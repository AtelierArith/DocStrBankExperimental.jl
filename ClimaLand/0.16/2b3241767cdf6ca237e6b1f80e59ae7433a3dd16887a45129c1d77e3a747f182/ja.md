```
clm_canopy_parameters(
    surface_space;
    regridder_type = :InterpolationsRegridder,
    extrapolation_bc = (
        Interpolations.Periodic(),
        Interpolations.Flat(),
        Interpolations.Flat(),
    ),
    lowres=use_lowres_clm(surface_space),
)
```

CLMおよびMODISデータに基づいて、NetCDFファイルからキャノピーの空間的に変化するパラメータを読み込み、Climaシミュレーションの`surface_space`によって定義されたグリッドに再グリッドします。ClimaCoreフィールドのNamedTupleを返します。

特に、このファイルは以下のフィールドを返します。

  * クランピング指数 Ω
  * PARおよびNIRバンドのアルベドおよび透過率
  * 葉角分布G関数パラメータ χl
  * メドリンg1
  * C3フラグ
  * VCmax25

値は各ポイントでの優勢PFTの値に対応します。

NetCDFファイルはClimaArtifactsに保存されており、その起源に関する詳細がそこに提供されています。キーワード引数`regridder_type`および`extrapolation_bc`は、(1)データにないClimaCoreポイントへの補間方法を変更し、(2)データの範囲を超えたポイントへの外挿方法を変更することによって、再グリッドに影響を与えます。キーワード引数lowresは、0.9x1.25または0.125x0.125解像度のCLMデータアーティファクトが使用されるかどうかを決定するフラグです。lowresフラグが提供されていない場合、surface_spaceに最も近い解像度のclmアーティファクトが使用されます。
