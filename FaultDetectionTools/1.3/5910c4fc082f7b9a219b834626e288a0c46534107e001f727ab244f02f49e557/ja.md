```
amdsyn(sysm::MDMModel; rdim, MDSelect, nullspace = true, simple = false, minimal = true, 
                       emtest = false, normalize = false, fast = true, 
                       sdeg, smarg, poles, HDesign, MDtol, MDGainTol, MDfreq, 
                       epsreg = 0.1, sdegzer, nonstd = 1, rtolinf= 0.0001, 
                       tcond, offset, atol, atol1, atol2, atol3, rtol) 
                       -> (Q::MDFilter, R::MDFilterIF, info)

与えられた複数合成モデル `sysm::MDMModel` に対して *近似モデル検出問題* (AMDP) を解決します。計算された安定で適切なフィルタオブジェクト `Q` と `R` は、AMDPの解を表すモデル検出フィルタを含んでいます。

返される名前付きタプル `info` には、`info.tcond`、`info.degs`、`info.MDperf`、`info.MDgap`、`info.HDesign`、および `info.nonstandard` のコンポーネントが含まれており、追加の合成関連情報が含まれています（以下を参照）。

`N` 個の安定なコンポーネントモデルを含む複数合成モデル `sysm` に対して、`i` 番目のコンポーネントシステム `sysm.sys[i]` は、次の形の記述子実現を持ちます： `sysm.sys[i] = (Ai-λEi,Bi,Ci,Di)`。対応する入力-出力形式は次の通りです。

```

yi = Gui(λ)*u + Gdi(λ)*di + Gwi(λ)*wi + Gvi(λ)*vi

```

ここで、ラプラス変換またはZ変換されたプラント出力 `yi`、制御入力 `u`、外乱入力 `di`、ノイズ入力 `wi`、および補助入力 `vi` があり、`Gui(λ)`、`Gdi(λ)`、`Gwi(λ)`、および `Gvi(λ)` は対応する伝達関数行列です。

モデル検出フィルタオブジェクト `Q` は、`Q.sys` に `N` 個のフィルタのバンクを含んでいます。`i` 番目のフィルタ `Q.sys[i]` は標準状態空間形式であり、全体の残差ベクトル `r := [r_1; r_2; ...; r_N]` の `i` 番目のコンポーネント（スカラーまたはベクトル） `r_i` を生成します。`i` 番目のフィルタの対応する入力-出力（実装）形式は次の通りです。

```

```
    r_i = Qyi(λ)*y + Qui(λ)*u ,
```

```

ここで、`Qyi(λ)` と `Qui(λ)` は、測定された出力と制御入力から `i` 番目の残差コンポーネントへの伝達関数行列です。測定された出力と制御入力の次元は、それぞれ整数 `Q.ny` と `Q.mu` に含まれています。

モデル検出フィルタ内部形式オブジェクト `R` は、`R.sys` に `N × N` の内部形式フィルタの配列を含んでいます。`(i,j)` 番目のコンポーネントフィルタ `R.sys[i,j]` は標準状態空間形式であり、残差信号 `r_ij` を生成し、入力-出力形式に対応します。

```

r_ij = Ruij(λ)*u + Rdij(λ)*dj + Rwij(λ)*wj + Rvij(λ)*vj ,

```

ここで、

```

| Ruij(λ) Rdij(λ) Rwij(λ) Raij(λ) | := |Qyi(λ) Qui(λ)]*| Guj(λ) Gdj(λ) Gwj(λ) Gaj(λ) |.                                                            |   I    0      0      0      |

```

AMDPの解は、`i` 番目のフィルタに対して `Ruii(λ) = 0`、`Rdii(λ) = 0`、`[Ruij(λ) Rdij(λ)]` $\neq$ `0` で `j` $\neq$ `i` の場合、さらに達成されたギャップの最大化を保証します（`info.MDgap` の説明を参照）。

さまざまなユーザーオプションは、キーワード引数を介して次のように指定できます。

`MDSelect = ifilt` は、設計するフィルタのインデックスをベクトル `ifilt` で指定します（デフォルト: `ifilt = 1:N`）。

`minimal = true` の場合（デフォルト）、最小次数フィルタ合成が行われ、`i = 1, ...,N` の各コンポーネントフィルタ `Q.sys[i]` と `i, j = 1, ...,N` の `R.sys[i,j]` が決定されます。一方、`minimal = false` の場合は、フルオーダー合成が行われます。

`HDesign = H` の場合、`H` はフル行ランクまたは空の設計行列 `H = [H_1, ..., H_N]` の `N` 次元配列であり、`H_i` は `i` 番目のコンポーネントフィルタの合成に使用される設計行列です（デフォルト: `HDesign = missing`）。

`rdim = q` は、ベクトル `q` を指定し、その `i` 番目のコンポーネント `q[i]` は `Q.sys[i]` の残差出力の数を指定します。`q` がスカラーの場合、すべてのコンポーネントが `q` に等しいベクトル `rdim` が仮定されます。`q[i]` のデフォルト値は次のように選択されます：`HDesign = missing` または `H_i` が空の場合、`q[i] = 1`、`minimal = true` の場合、または `minimal = false` の場合は `Q.sys [i]` の合成に使用されるヌル空間基底ベクトルの数です。`H_i` がフル行ランク設計行列を指定する場合、`q[i]` は `H_i` の行次元です。

`emdtest = false` の場合（デフォルト）、モデル検出性テストには入力チャネルのみが使用されます。`emdtest = true` の場合、制御および外乱入力チャネルの両方を使用して拡張モデル検出性テストが実施されます。

`MDfreq = ω` は、強いモデル検出性チェックのための実周波数値のベクトルまたはスカラー実周波数値を指定します（デフォルト: `MDfreq = missing`）。

`nullspace = false` の場合（デフォルト）、`i` 番目のコンポーネントシステムに外乱入力がない場合、`i` 番目のフィルタの合成にはフルオーダーオブザーバに基づくヌル空間基底が使用されます。そうでない場合は、最小適切なヌル空間基底が使用されます。`nullspace = true` の場合、モデル検出フィルタの合成には最小適切なヌル空間基底が使用されます。

`simple = true` の場合、合成には単純な適切なヌル空間基底が使用されます。`i` 番目のフィルタの合成に使用される基底ベクトルの次数は `info.deg[i]` に提供されます。`simple = false` の場合（デフォルト）、単純な基底は計算されません。

`offset = β` は、極の安定性を評価するための境界オフセット `β` を指定します。したがって、連続時間システムの安定性のためには、すべての極の実部が最大で `-β` でなければならず、離散時間システムの安定性のためには、すべての極の絶対値が最大で `1-β` でなければなりません。`β` に使用されるデフォルト値は `sqrt(ϵ)` であり、`ϵ` は作業機械精度です。

`smarg = α` は、極の安定性領域 `Cs` を定義する安定性マージンを指定します。連続時間システムの場合、`Cs` は実部が最大で `α` の複素数の集合であり、離散時間システムの場合、`Cs` は絶対値が最大で `α < 1` の複素数の集合です（すなわち、原点を中心とした半径 `α` の円の内部）。`smarg` が欠落している場合、使用されるデフォルト値は、連続時間システムの場合は `α = -β`、離散時間システムの場合は `α = 1-β` であり、ここで `β` はキーワード引数 `offset = β` で指定された境界オフセットです。

`sdeg = γ` は、フィルタ `Q` と `R` の極のための指定された安定性次数です（デフォルト: 連続時間システムの極の実部に対して `γ = -0.05`、離散時間システムの極の絶対値に対して `γ = 0.95`）。

`poles = v` は、フィルタ `Q` と `R` に割り当てる安定性領域 `Cs` 内の望ましい極の複素共役セットを含む複素ベクトル `v` を指定します（デフォルト: `poles = missing`）。

`tcond = tcmax` は、使用される非直交変換の最大許容条件数 `tcmax` を指定します（デフォルト: `tcmax = 1.e4`）。

`MDtol = tol1` は、モデル検出性チェックのための閾値 `tol1` を指定します（デフォルト: `tol1 = 0.0001`）。

`MDGainTol = tol2` は、強いモデル検出性チェックのための閾値 `tol2` を指定します（デフォルト: `tol2 = 0.01`）。

`normalize = false` の場合（デフォルト）、`i` 番目のコンポーネントフィルタ `Q.sys[i]` は、`j = 1, ..., N` の `R.sys[i,j]` の最小ゲインが1になるようにスケーリングされます。`normalize = true` の場合、コンポーネントフィルタの標準正規化が行われ、`R.sys[1,j]` と `R.sys[j,1]` のゲインが等しくなります。このオプションは、`ifilt[1] = 1` の場合にのみ可能です（`MDSelect` を参照）。

`epsreg = ϵ` は、正則化パラメータ `ϵ` の値を指定します（デフォルト: `ϵ = 0.1`）。

`sdegzer = δ` は、ゼロシフトのための指定された安定性次数 `δ` を指定します（デフォルト: 連続時間システム `sysf.sys` に対して `δ = −0.05`、離散時間システム `sysf.sys` に対して `δ = 0.95`）。

`nonstd = job` は、非標準最適化問題を処理するオプションを指定します。

```

job = 1 – 擬似共外共内因子分解を使用（デフォルト）;   job = 2 – 正則化パラメータ `ϵ` を使用した修正共外共内因子分解;   job = 3 – ウィーナーホフ型共外共内因子分解を使用;   job = 4 – 安定化パラメータ `δ` を使用して非最小位相因子のゼロシフトを行うウィーナーホフ型共外共内因子分解を使用;   job = 5 – 非最小位相因子の正則化を使用したウィーナーホフ型共外共内因子分解を使用。

```

実施された削減におけるランクの決定は、`fast = true` の場合（デフォルト）には列ピボットを伴うランクを明らかにするQR分解に基づいており、`fast = false` の場合にはより信頼性の高いSVD分解に基づいています。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ状態空間行列 `Ai`、`Bi`、`Ci`、および `Di` の非ゼロ要素の絶対許容誤差、`Ei` の非ゼロ要素の絶対許容誤差、および上記のすべての行列の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `ni*ϵ` であり、ここで `ϵ` は作業機械エプシロンで、`ni` はシステム `sysm.sys[i]` の次数です。キーワード引数 `atol3` は、可観測性テストのための絶対許容誤差です（デフォルト: 内部で決定された値）。キーワード引数 `atol` は、同時に `atol1 = atol`、`atol2 = atol`、および `atol3 = atol` を設定するために使用できます。

結果として得られる名前付きタプル `info` には `(tcond, degs, MDperf, MDgap, HDesign, nonstandard)` が含まれています。ここで：

`info.tcond` は、使用された非直交変換行列の条件数の最大値です。`info.tcond >= tcmax` の場合は警告が発行されます。

`info.degs` は、`i` 番目のコンポーネントの合成に使用された単純なヌル空間基底の基底ベクトルの次数を含む整数ベクトルの `N` 次元ベクトルです（`simple = true` の場合）、および同等の多項式ヌル空間基底の基底ベクトルの次数（`simple = false` の場合）。

`info.MDperf` は、モデル検出フィルタの関連内部表現のピークゲインを表す結果の距離マッピング性能を含む `N × N` 配列です。`(i,j)` 番目のコンポーネントフィルタ `R.sys[i,j]` が次の入力-出力形式を持つ場合：

```

rij = Ruij(λ)*u + Rdij(λ)*dj + Rwij(λ)*wj + Rvij(λ)*vj ,

```

その場合、`(i,j)` 番目の性能ゲインは、`emdtest = false` の場合（デフォルト）には `info.MDperf[i,j] = ||Ruij(λ)||∞` と評価され、`emdtest = true` の場合には `info.MDperf[i,j] = ||[Ruij(λ) Rdij(λ)]||∞` と評価されます。`MDfreq = ω` の場合、各ゲイン `info.MDperf[i,j]` は、`ω` のすべての周波数に対して評価された2ノルムの点ごとのゲインの最大値を表します。

`info.MDgap` は、達成されたノイズギャップの `N` 次元ベクトルであり、`i` 番目のギャップは `info.MDgap[i] = β[i]/γ[i]` として計算されます。ここで、`β[i] = min(||Rij(λ)||∞` for `i` $\neq$ `j`) であり、`γ[i] = ||Rwii(λ)||∞` です。`Rij(λ)` は、`emtest = false` の場合（デフォルト）には `Rij(λ) = Ruij(λ)` と定義され、`emtest = true` の場合には `Rij(λ) = [Ruij(λ) Rdij(λ)]` です。`MDfreq = ω` の場合、`ω` は与えられた実周波数値のベクトルであり、各ゲイン `β[i]` は `ω` のすべての周波数に対して評価された2ノルムの点ごとのゲインの最大値を表します。

`info.HDesign` は、`i` 番目のモデル検出フィルタの合成に使用される設計行列 `H_i` を含む `N` 次元ベクトルです。

`info.nonstandard` は、`i` 番目のフィルタの合成に非標準最適化問題が関与している場合は `true`、そうでない場合は `false` である `N` 次元ベクトルです。

*メソッド:* 近似モデル検出問題を解決するために、手続きAMDの拡張が実装されています。この手続きは、モデル検出フィルタのヌル空間ベースの合成方法に依存しています。

*参考文献:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.                Springer Verlag, 2017; sec. 5.2.

[2] A. Varga, Least order fault and model detection using multi-models.         IEEE CDC'09, Shanghai, China, 2009.
```
