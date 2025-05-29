```julia
modelage(mineral::ZirconHe, Tsteps, [ρᵣ], dm::ZRDAAM)
modelage(mineral::ApatiteHe, Tsteps, [ρᵣ], dm::RDAAM)
modelage(mineral::SphericalHe, Tsteps, dm::Diffusivity)
modelage(mineral::PlanarHe, Tsteps, dm::Diffusivity)
```

与えられたt-T経路（時間のための`mineral.tsteps`と温度のための`Tsteps`で指定され、時間解像度は`step(mineral.tsteps)`）を経験したジルコン、アパタイト、または他の鉱物の予測されるバルクU-Th/He年齢を計算します。これは、空間解像度`mineral.dr`で半径（または半幅）`mineral.r`の球状（または平面スラブ）粒子のためのCrank-Nicolson拡散解を使用します。

球状実装は、Ketcham, 2005の球状鉱物結晶からの拡散のためのCrank-Nicolson解に基づいています（doi: 10.2138/rmg.2005.58.11）。
