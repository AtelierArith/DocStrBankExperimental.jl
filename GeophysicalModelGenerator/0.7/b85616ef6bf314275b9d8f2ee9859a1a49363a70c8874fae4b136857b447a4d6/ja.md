```
LithosphericTemp(Tsurface=0.0, Tpot=1350.0, dTadi=0.5,
                    ubound="const", lbound="const, utbf = 50.0e-3, ltbf = 10.0e-3,
                    age = 120.0, dtfac = 0.9, nz = 201,
                    rheology = example_CLrheology()
                )
```

変動する熱パラメータを含む1D温度プロファイル[C]を計算し、温度プロファイルをボックスに線形補間します。熱パラメータはrheologyで定義され、リソスフェアの構造はLithosphericPhases()によって定義されます。

# パラメータ

  * Tsurface  : 表面温度 [C]
  * Tpot      : 潜在マントル温度 [C]
  * dTadi     : 断熱勾配 [K/km]
  * ubound    : 上部熱境界条件 ["const","flux"]
  * lbound    : 下部熱境界条件 ["const","flux"]
  * utbf      : 上部熱フラックス [W/m]; ubound == "flux" の場合
  * ltbf      : 下部熱フラックス [W/m]; lbound == "flux" の場合
  * age       : リソスフェアの年齢 [Ma]
  * dtfac     : T_ageを計算するための拡散安定性基準
  * nz        : ボックス内の1Dプロファイルのグリッド間隔
  * rheology  : 各相の熱パラメータを含む構造 [デフォルト example_CLrheology]
