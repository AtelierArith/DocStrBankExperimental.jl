```
ammsyn(sysf::FDIModel, sysr::FDIFilterIF; nullspace = true, simple = false, mindeg = false, 
                       regmin = true, normalize = "infnorm", H2syn = false, reltol = 1.e-4, 
                       sdeg, smarg, poles, freq, HDesign, tcond, offset, 
                       atol, atol1, atol2, atol3, rtol, fast = true) 
                       -> (Q::FDFilter, R::FDFilterIF, info)
```

与えられた合成モデル `sysf::FDIModel` と安定した参照フィルタのバンク `sysr::FDIFilterIF` に対して、*近似モデルマッチング問題* (AMMP) を解決します。計算された安定かつ適切なフィルタオブジェクト `Q` と `R` は、AMMP の成分ごとの解を表す故障検出フィルタのバンクを含み、それぞれの内部形式を持ちます。

返される名前付きタプル `info` には、`info.tcond`、`info.degs`、`info.M`、`info.freq`、`info.HDesign`、`info.nonstandard`、`info.gammaopt0`、`info.gammaopt`、および `info.gammasub` のコンポーネントが含まれ、追加の合成関連情報が含まれています（詳細は以下を参照）。

連続時間または離散時間システム `sysf.sys` は、標準または記述子状態空間形式 `sysf.sys = (A-λE,B,C,D)` にあり、これは入力-出力形式に対応します。

```
   y = Gu(λ)*u + Gd(λ)*d + Gf(λ)*f + Gw(λ)*w + Ga(λ)*aux,
```

ラプラス変換または Z 変換されたプラント出力 `y`、制御入力 `u`、外乱入力 `d`、故障入力 `f`、ノイズ入力 `w`、および補助入力 `aux` があり、`Gu(λ)`、`Gd(λ)`、`Gf(λ)`、`Gw(λ)`、および `Ga(λ)` はそれぞれの伝達関数行列です。制御、外乱、故障、ノイズ、および補助入力のインデックスは、関連する整数ベクトル `sysf.controls`、`sysf.disturbances`、`sysf.faults`、`sysf.noise`、および `sysf.aux` に含まれています。

`sysr` にパックされた連続時間または離散時間の参照フィルタは、標準または記述子状態空間形式にあり、`i` 番目のフィルタ `sysr.sys[i] = (Ari-λEri,Bri,Cri,Dri)` は入力-出力形式に対応します。

```
   yri = Mrui(λ)*u + Mrdi(λ)*d + Mrfi(λ)*f + Mrwi(λ)*w + Mrai(λ)*aux,
```

ラプラス変換または Z 変換された参照フィルタ出力 `yri`、制御入力 `u`、外乱入力 `d`、故障入力 `f`、ノイズ入力 `w`、および補助入力 `aux` があり、`Mrui(λ)`、`Mrdi(λ)`、`Mrfi(λ)`、`Mrwi(λ)`、および `Mrai(λ)` はそれぞれの伝達関数行列です。制御、外乱、故障、ノイズ、および補助入力のインデックスは、関連する整数ベクトル `sysr.controls`、`sysr.disturbances`、`sysr.faults`、`sysr.noise`、および `sysr.aux` に含まれています。上記のベクトルのいずれかが空である場合、対応する伝達関数行列は null と見なされます。

故障検出および隔離フィルタオブジェクト `Q` は、その `i` 番目のコンポーネント `Q.sys[i]` に、残差信号の `i` 番目のコンポーネント `ri` を生成する標準状態空間形式の結果フィルタを含みます。対応する入力-出力（実装）形式は次のとおりです。

```
        ri = Qyi(λ)*y + Qui(λ)*u
```

ここで `Qyi(λ)` と `Qui(λ)` は、出力および制御入力から残差への伝達関数行列です。出力および制御入力のインデックスは、整数ベクトル `Q.outputs` と `Q.controls` に含まれています。

定義しましょう。

```
  Ge(λ) = | Gu(λ) Gd(λ) Gf(λ) Gw(λ) Ga(λ) |,  Mri(λ) = | Mrui(λ) Mrdi(λ) Mrfi(λ) Mrwi(λ) Mrai(λ) | . 
          |  I     0     0     0     0    |
```

標準的な場合、`Ge(λ)` は安定性領域の境界にゼロを持たず、各結果コンポーネント安定フィルタ `Qi(λ) := |Qyi(λ) Qui(λ)|` は `Qi(λ) = Q0i(λ)` であり、ここで `Q0i(λ)` は H∞-または H2-ノルム誤差最小化問題の最適解です。

```
gammaopt0i = ||Q0i(λ)*Ge(λ)-Mi(λ)*Mri(λ)|| = min,         (1)
```

ここで `Mi(λ) = M0i(λ)` は次のように選ばれる更新因子です：H∞ ノルムを使用する場合は `M0i(λ) = I`、H2 ノルムを使用する場合は、離散時間システムの場合は `M0i(λ) = I`、連続時間システムの場合は、安定で対角的かつ可逆な伝達関数行列 `M0i(λ)` が決定され、有限の H2 ノルムの存在が保証されます。

非標準的な場合、`Ge(λ)` は安定性領域の境界にゼロを持ち、各結果最適コンポーネントフィルタ `Q0i(λ)` は H∞-または H2-ノルム誤差最小化問題 (1) を解決しますが、安定性がないか不適切である可能性があります。2 番目の更新因子 `M1i(λ)` が決定され、`M0i(λ)` と同じ特性を持ち、計算された安定かつ適切なフィルタ `Qi(λ) := M1i(λ)*Q0i(λ)` が、更新された H∞-または H2-ノルム誤差最小化問題のサブ最適解を表すことが保証されます。このとき、達成されたサブ最適モデルマッチング性能は次のようになります。

```
gammasubi = ||Qi(λ)*Ge(λ)-Mi(λ)*Mri(λ)|| ,            (2)
```

ここで `Mi(λ) := M1i(λ)*M0i(λ)` です。更新された H∞-または H2-ノルム誤差最小化問題の*最適*解 `Qti(λ)` は次のようになります。

```
gammaopti = ||Qti(λ)*Ge(λ)-Mi(λ)*Mri(λ)|| = min ,     (3)
```

これも安定性がないか不適切である可能性があります。`gammaopt0i`、`gammaopti`、および `gammasubi` の値は、それぞれベクトル `info.gammaopt0`、`info.gammaopt`、および `info.gammasub` の `i` 番目のコンポーネントに返されます。

故障検出および隔離フィルタ内部形式オブジェクト `R` は、その `i` 番目のコンポーネント `R.sys[i]` に、残差信号の `i` 番目のコンポーネント `ri` を生成する標準状態空間形式のフィルタの結果内部形式を含み、入力-出力形式に対応します。

```
   ri = Rui(λ)*u + Rdi(λ)*d + Rfi(λ)*f + Rwi(λ)*w + Rai(λ)*aux ,
```

ここで 

```
   | Rui(λ) Rdi(λ) Rfi(λ) Rwi(λ) Rai(λ) | = Qi(λ)*Ge(λ).
```

結果フィルタ `R.sys` の入力 `u`、`d`、`f`、`w`、および `aux` のインデックスは、整数ベクトル `R.controls`、`R.disturbances`、`R.faults`、`R.noise`、および `R.aux` に含まれています。結果の `Mi(λ)` の状態空間実現は、ベクトル `info.M` の `i` 番目のコンポーネントに返されます。

さまざまなユーザーオプションは、キーワード引数を介して次のように指定できます。

`H2syn = false`（デフォルト）の場合、H∞-ノルムに基づく合成が実行され、`H2syn = true` の場合、H2-ノルムに基づく合成が実行されます。

`reltol = tol` は、γ-反復の所望の精度のための相対許容誤差 `tol` を指定します（デフォルト：`tol = 1.e-4`）。

`mindeg = true` の場合、可能であれば最小次数フィルタ合成が実行され、`minimal = false`（デフォルト）の場合は最小次数合成は実行されません。

`regmin = true`（デフォルト）の場合、`sysr.controls` および/または `sysr.disturbances` が空である場合に、最小次数の左消去器 `Nl(λ)` を選択して正則化が実行されます。`regmin = false` の場合、正則化は `G(λ) = [Gu(λ) Gd(λ); I 0 ]` の最小左零空間基底として左消去器 `Nl(λ)` を選択することによって実行されます。

`HDesign = H` がフル行ランク設計行列のベクトルである場合、`H[i]*Nl(λ)` が `i` 番目のフィルタの合成のための左消去器として使用されます（デフォルト：`HDesign = missing`）。

`nullspace = true`（デフォルト）の場合、`sysr.controls` および/または `sysr.disturbances` が空である場合、初期削減ステップで最小適切な零空間基底が使用されます。`nullspace = false` の場合、`sysr.controls` および/または `sysr.disturbances` が空である場合、初期削減ステップでフルオーダーのオブザーバベースの零空間基底が使用されます。このオプションは、外乱入力のない適切なシステムにのみ使用できます。`nullspace` オプションは、両方の `sysr.controls` と `sysr.disturbances` が非空である場合は無視されます。

`simple = true` の場合、合成のための左消去器として単純な適切な零空間基底が使用されます。基底ベクトルの次数は `info.deg` に提供されます。`simple = false`（デフォルト）の場合、最小適切な零空間基底が計算されます。

`offset = β` は、極の安定性を評価するための境界オフセット `β` を指定します。したがって、連続時間システムの安定性のためには、極のすべての実部が最大で `-β` でなければならず、離散時間システムの安定性のためには、極のすべてのモジュールが最大で `1-β` でなければなりません。`β` に使用されるデフォルト値は `sqrt(ϵ)` であり、ここで `ϵ` は作業機械精度です。

`smarg = α` は、極の安定性領域 `Cs` を定義する安定性マージンを指定します。連続時間システムの場合、`Cs` は実部が最大で `α` の複素数の集合であり、離散時間システムの場合、`Cs` はモジュールが最大で `α < 1` の複素数の集合です（すなわち、原点を中心とした半径 `α` の円の内部）。`smarg` が欠落している場合、使用されるデフォルト値は、連続時間システムの場合は `α = -β`、離散時間システムの場合は `α = 1-β` です。ここで `β` はキーワード引数 `offset = β` で指定された境界オフセットです。

`sdeg = γ` は、フィルタ `Q` と `R` の極のための指定された安定性次数です（デフォルト：連続時間システムの極の実部に対して `γ = -0.05`、離散時間システムの極の大きさに対して `γ = 0.95`）。

`poles = v` は、フィルタ `Q` と `R` に割り当てる安定性領域 `Cs` 内の望ましい極の複素共役セットを含む複素ベクトル `v` を指定します（デフォルト：`poles = missing`）。

`tcond = tcmax` は、使用される非直交変換の最大許容条件数 `tcmax` を指定します（デフォルト：`tcmax = 1.e4`）。

`freq = val` は、フルカラムランク（すなわち、左可逆性）解決条件をチェックするために使用されるテスト周波数の値を指定します（デフォルト：`(0,1)` の範囲でランダムに生成されます）。使用される `freq` の値は `info.freq` に返されます。

`normalize = job` は、更新行列 `Mi(λ)` の対角要素の正規化オプションを次のように指定します。

```
  job = "gain"    – ゼロ-極-ゲイン表現のゲインでスケールする;
  job = "dcgain"  – DCゲインでスケールする;
  job = "infnorm" – 無限ノルムの値でスケールする（デフォルト）。
```

実行された削減におけるランクの決定は、`fast = true` の場合はカラムピボッティングを伴うランクを明らかにする QR 分解に基づき、`fast = false` の場合はより信頼性の高い SVD 分解に基づきます。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ `A`、`B`、`C`、`D` の非ゼロ要素の絶対許容誤差、`E` の非ゼロ要素の絶対許容誤差、および `A`、`B`、`C`、`D` および `E` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は作業機械エプシロンで、`n` はシステム `sysf.sys` の次数です。キーワード引数 `atol3` は可観測性テストの絶対許容誤差です（デフォルト：内部で決定された値）。キーワード引数 `atol` は、同時に `atol1 = atol`、`atol2 = atol`、および `atol3 = atol` を設定するために使用できます。

結果の名前付きタプル `info` には `(tcond, degs, M, freq, HDesign, gammaopt0, gammaopt, gammasub, nonstandard)` が含まれます。ここで：

`info.tcond` は、使用された非直交変換行列の条件数の最大値です。`info.tcond >= tcmax` の場合は警告が発行されます。

`info.degs` は、`G(λ) := [ Gu(λ) Gd(λ); I 0]` の左最小多項式零空間基底の次数を増加順に含む整数ベクトルです（`[Gu(λ) Gd(λ)]` の状態空間実現が最小である場合）。

`info.M` は、`i` 番目のシステム `info.M[i]` が、`i` 番目の AMMP を解決するために使用された安定かつ可逆な更新フィルタを含む記述子システムのベクトルであり、対角伝達関数行列 `Mi(λ)` を持ちます。

`info.freq` は、左可逆性をチェックするために使用された周波数であり（周波数ベースの左可逆性チェックが実行されなかった場合は `missing` に設定されます）。

`info.HDesign` は設計行列 `H` のベクトルであり、`H[i]` は故障検出フィルタ `Q` の `i` 番目のコンポーネントの合成に使用された設計行列です。`H[i]` は、設計行列が関与していない場合は空の行列です。

`info.gammaopt0` は、`i` 番目の元の問題 (1) に対する最適性能 `gammaopt0i` であるベクトルです。

`info.gammaopt` は、`i` 番目の更新された問題 (3) に対する最適性能 `gammaopti` であるベクトルです。

`info.gammasub` は、(2) におけるサブ最適性能 `gammasubi` であるベクトルです。

`info.nonstandard` は、非標準問題の場合は `true` に設定され（すなわち、`Ge(λ)` が安定性領域の境界にゼロを持つ）、標準問題の場合は `false` に設定されます（すなわち、`Ge(λ)` が安定性領域の境界にゼロを持たない）。

*メソッド:* 合成手順 AMMS が [1] から使用され、コンポーネントフィルタが決定されます。手順 AMMS は、[2] で提案された近似モデルマッチング合成法に依存しています。計算の詳細については [3] を参照してください。

*参考文献:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.                Springer Verlag, 2017; sec. 5.6.

[2] A. Varga, Integrated computational algorithm for solving      H_inf-optimal FDI problems. In Proc. of the IFAC World Congress,      Milano, Italy, pp. 10187–10192, 2011.

[3] A. Varga. Descriptor system techniques in solving H_2/H-Inf-optimal     fault detection and isolation problems". In L. T. Biegler,       S. L. Campbell, and V. Mehrmann (Eds.), Control and Optimization      with Differential-Algebraic Constraints, vol. 23 of Advances in      Design and Control, pp. 105–125. SIAM, 2012.  ```
