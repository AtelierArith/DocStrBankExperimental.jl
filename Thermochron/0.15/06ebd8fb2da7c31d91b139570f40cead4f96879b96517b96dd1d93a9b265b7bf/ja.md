```julia
modelage(mineral::SphericalAr, Tsteps, dm::Diffusivity)
modelage(mineral::PlanarAr, Tsteps, dm::Diffusivity)
```

与えられた t-T パス（時間のための `mineral.tsteps` と温度のための `Tsteps` で指定）を経験した鉱物の予測されたバルク K/Ar 年齢を計算します。時間解像度は `step(mineral.tsteps)` で、半径（または半幅） `mineral.r` の球状（または平面スラブ）粒子の Crank-Nicholson 拡散解法を使用し、空間解像度は `mineral.dr` です。

球状の実装は、Ketcham, 2005 における球状鉱物結晶からの拡散に対する Crank-Nicholson 解法に基づいています（doi: 10.2138/rmg.2005.58.11）。
