```
glasol(sysg, sysf[, γ]; L2sol = false, nehari = false, reltol = 0.0001, mindeg = false, poles, sdeg, 
       fast = true, offset = β, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (sysx, info)
```

記述子システム `sysg = (Ag-λEg,Bg,Cg,Dg)` と `sysf = (Af-λEf,Bf,Cf,Df)` に対して、伝達関数行列 `G(λ)` と `F(λ)` をそれぞれ持つ記述子システム `sysx` を決定します。ここで、`X(λ)` は線形有理方程式 `X(λ)G(λ) = F(λ)` の近似解であり、最小誤差ノルム ${\small \text{mindist} := \min \|X(λ)G(λ) - F(λ)\|}$ を達成します。得られた `X(λ)` はすべての極が安定であるか、安定性領域 `Cs` の境界上にあります。`L2sol = false`（デフォルト）の場合、`L∞`-ノルム最適解が計算され、`L2sol = true` の場合は `L2`-ノルム最適解が計算されます。`sysg` と `sysf` は、安定性領域 `Cs` の境界上に極を持ってはいけません。

もし `γ > 0` が望ましいサブ最適性の度合いである場合、`γ`-サブ最適モデルマッチング問題

$$
     \text{mindist} := \|X(λ)G(λ) - F(λ) \| < γ
$$

が解決され、`mindist` は達成されたサブ最適距離です。

次の呼び出しは

```
glasol(sysgf[, pf[, γ]]; L2sol = false, nehari = false, reltol = 0.0001, mindeg = false, poles, sdeg, 
       fast = true, offset = β, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (sysx, info)
```

複合記述子システム `sysgf = (A-λE,B,[Cg; Cf],[Dg; Df])` を使用し、ここで `Cf` と `Df` は `pf` 行を持ち、記述子システム `sysg = (A-λE,B,Cg,Dg)` と `sysf = (A-λE,B,Cf,Df)` を定義します（すなわち、`Ag-λEg = Af-λEf = A-λE` および `Bg = Bf = B`）。`sysgf` は安定性領域 `Cs` の境界上に極を持ってはいけません。

もし `nehari = true` の場合、最適またはサブ最適のネハリ近似が基礎となる*最小距離問題*（`LDP`）を解決するために使用されます。もし `nehari = false`（デフォルト）の場合、基礎となる `LDP` [2] において `γ`-反復を使用して最適解が計算されます。

もし `mindeg = true` の場合、最小次数の解が決定されます（可能であれば）、一方で `mindeg = false`（デフォルト）の場合は非最小次数の特定の解が決定されます。

得られた名前付きタプル `info` には追加情報が含まれます：`info.nrank` は `G(λ)` の通常のランク、`info.nl` は解 `X(λ)` の自由に割り当て可能な極の数、`info.mindist` は達成された近似誤差ノルム、`info.nonstandard` は `G(λ)` が安定性領域の境界上にゼロを持つ場合に `true` となり、`G(λ)` が安定性領域の境界上にゼロを持たない場合は `false` となります。

キーワード引数 `reltol` は、基礎となる最小距離問題を解決するために使用される `γ`-反復の望ましい精度に対する相対許容誤差を指定します。反復は、最適距離の最大 $γ_u$ と最小 $γ_l$ の現在の推定値が ${\small γ_u-γ_l < \text{reltol}* \text{gap}}$ を満たすまで行われます。ここで `gap` は誤差ギャップの初期推定値です。

安定性領域 `Cs` の境界上に極が存在するかどうかを評価するために、キーワードパラメータ `offset = β` を介して境界オフセット `β` を指定できます。したがって、連続時間設定の場合、`Cs` の境界には実部が区間 `[-β,β]` にある複素数が含まれ、離散時間設定の場合、`Cs` の境界には絶対値が区間 `[1-β,1+β]` にある複素数が含まれます。`β` に使用されるデフォルト値は `sqrt(ϵ)` であり、ここで `ϵ` は作業機械精度です。

キーワード引数として指定されたベクトル `poles` は、極の望ましい値を `sysx` に指定するために、極の望ましい安定性度 `sdeg` を強制することと併せて使用できます。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ `Ag`、`Af`、`A`、`Bg`、`Bf`、`Cg`、`Cf`、`Dg`、`Df` の非ゼロ要素に対する絶対許容誤差、`Eg`、`Ef` の非ゼロ要素に対する絶対許容誤差、そして上記のすべての行列の非ゼロ要素に対する相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は作業機械エプシロンで、`n` はシステム `sysg` の次数です。キーワード引数 `atol` は、同時に `atol1 = atol` および `atol2 = atol` を設定するために使用できます。

基礎となるペンシル操作アルゴリズムにおけるランクの決定は、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づき、`fast = false` の場合はより信頼性の高いSVD分解に基づきます。

*メソッド:*  [1] のアプローチの拡張が記述子システムに使用されます。

*参考文献:*

[1]  B. A. Francis. A Course in H-infinity Theory,         Vol. 88 of Lecture Notes in Control and Information Sciences,         Springer-Verlag, New York, 1987.

[2] C.-C. Chu, J. C. Doyle, and E. B. Lee.     The general distance problem in H∞  optimal control theory,     Int. J. Control, vol 44, pp. 565-596, 1986. ```
