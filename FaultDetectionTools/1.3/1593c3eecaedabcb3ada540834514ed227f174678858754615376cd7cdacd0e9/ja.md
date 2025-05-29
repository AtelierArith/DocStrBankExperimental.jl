```
S = fdigenspec(sysf::FDIModel; sdeg, FDtol, FDGainTol, FDfreq, atol, atol1, atol2, atol3, rtol, fast = true)
```

与えられた合成モデル `sysf` に対して、加法的故障のためのすべての達成可能な仕様 `S` を生成します。結果として得られるバイナリ行列 `S` の各行には、線形故障検出フィルタ（例えば、関数 [`efdisyn`](@ref) の助けを借りて得られるもの）を使用して達成可能な非ゼロ仕様（または故障署名）が含まれています。

`FDFreq = freq` は、強検出可能性チェックのための実周波数値のベクトルまたはスカラー実周波数値を指定します（デフォルト: `FDFreq = missing`）。

`FDtol = tol1` は、弱仕様を評価するための閾値 `tol1` を指定します（関数 [`fditspec`](@ref) も参照）（デフォルト: `tol1 = 0.0001`）。

`FDGainTol = tol2` は、強仕様を評価するための閾値 `tol2` を指定します。すなわち、指定された周波数値 `freq` に対する非ゼロ周波数応答ゲインの閾値です（関数 [`fdisspec`](@ref) も参照）（デフォルト: `tol2 = 0.01`）。

キーワード引数 `sdeg = β` は、内部生成された候補フィルタの極のための所定の安定度 `β` を指定します。連続時間の場合、フィルタの極の実部は `β` 以下でなければならず、離散時間の場合、フィルタの極の大きさは `β` 以下でなければなりません。`sdeg = missing` の場合、`FDFreq = missing` であれば安定化は行われません。`sdeg = missing` かつ `FDFreq = freq` の場合、次のデフォルト値が使用されます: 連続時間の場合 `β = -0.05`、離散時間の場合 `β = 0.95`。

実行された削減におけるランクの決定は、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づき、`fast = false` の場合はより信頼性の高いSVD分解に基づきます。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ、`A`、`B`、`C`、`D` の非ゼロ要素の絶対許容誤差、`E` の非ゼロ要素の絶対許容誤差、および `A`、`B`、`C`、`D` および `E` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は作業用マシンエプシロン、`n` はシステム `sysf.sys` の次数です。キーワード引数 `atol3` は可観測性テストのための絶対許容誤差です（デフォルト: 内部で決定された値）。キーワード引数 `atol` は、同時に `atol1 = atol`、`atol2 = atol` および `atol3 = atol` を設定するために使用できます。

*方法:* 手続き GENSPEC が [1] に実装されています。null空間法 [2] は、候補の故障検出および隔離フィルタを生成するために再帰的に使用され、その内部形式は、`freq = missing` の場合は達成可能な弱仕様に対応する構造行列を提供し、`freq` に含まれる周波数の強仕様に対応します。この生成方法については [3] でも説明されています。

*参考文献:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.       Springer Verlag, 2017; sec. 5.4.

[2] A. Varga, On computing nullspace bases – a fault detection perspective.        Proc. IFAC 2008 World Congress, Seoul, Korea, pages 6295–6300, 2008.

[3] A. Varga, On computing achievable fault signatures. Proc. SAFEPROCESS'2009, Barcelona, Spain.  ```
