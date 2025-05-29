```
emmsyn(sysf::FDIModel, sysr::FDIFilterIF; nullspace = true, simple = false, minimal = true, regmin = true, normalize = "gain", 
                       sdeg, smarg, poles, freq, HDesign, tcond, offset, 
                       atol, atol1, atol2, atol3, rtol, fast = true) 
                       -> (Q::FDIFilter, R::FDIFilterIF, info)
```

与えられた合成モデル `sysf::FDIModel` と安定した参照フィルタのバンク `sysr::FDIFilterIF` に対して、*正確なモデルマッチング問題* (EMMP) を解決します。計算された安定かつ適切なフィルタオブジェクト `Q` と `R` は、EMMP の成分ごとの解を表す故障検出フィルタのバンクを含み、それぞれの内部形式を持ちます。

返される名前付きタプル `info` には、`info.tcond`、`info.degs`、`info.M`、`info.freq`、および `info.HDesign` のコンポーネントが含まれ、追加の合成関連情報が含まれます（以下を参照）。

連続時間または離散時間システム `sysf.sys` は、標準または記述子状態空間形式 `sysf.sys = (A-λE,B,C,D)` にあり、これは入力-出力形式に対応します。

```
   y = Gu(λ)*u + Gd(λ)*d + Gf(λ)*f + Gw(λ)*w + Ga(λ)*aux,
```

ラプラス変換または Z 変換されたプラント出力 `y`、制御入力 `u`、外乱入力 `d`、故障入力 `f`、ノイズ入力 `w`、および補助入力 `aux` があり、`Gu(λ)`、`Gd(λ)`、`Gf(λ)`、`Gw(λ)`、および `Ga(λ)` は対応する伝達関数行列です。制御、外乱、故障、ノイズ、および補助入力のインデックスは、関連する整数ベクトル `sysf.controls`、`sysf.disturbances`、`sysf.faults`、`sysf.noise` および `sysf.aux` に含まれています。

`sysr` にパックされた連続時間または離散時間の参照フィルタは、標準または記述子状態空間形式にあり、`i` 番目のフィルタ `sysr.sys[i] = (Ari-λEri,Bri,Cri,Dri)` は入力-出力形式に対応します。

```
   yri = Mrui(λ)*u + Mrdi(λ)*d + Mrfi(λ)*f + Mrwi(λ)*w + Mrai(λ)*aux,
```

ラプラス変換または Z 変換された参照フィルタ出力 `yri`、制御入力 `u`、外乱入力 `d`、故障入力 `f`、ノイズ入力 `w`、および補助入力 `aux` があり、`Mrui(λ)`、`Mrdi(λ)`、`Mrfi(λ)`、`Mrwi(λ)`、および `Mrai(λ)` は対応する伝達関数行列です。制御、外乱、故障、ノイズ、および補助入力のインデックスは、関連する整数ベクトル `sysr.controls`、`sysr.disturbances`、`sysr.faults`、`sysr.noise` および `sysr.aux` に含まれています。上記のベクトルのいずれかが空である場合、対応する伝達関数行列は null と見なされます。

故障検出および隔離フィルタオブジェクト `Q` は、その `i` 番目のコンポーネント `Q.sys[i]` に、残差信号の `i` 番目のコンポーネント `ri` を生成するフィルタを標準状態空間形式で含みます。対応する入力-出力（実装）形式は次のとおりです。

```
        ri = Qyi(λ)*y + Qui(λ)*u
```

ここで、`Qyi(λ)` と `Qui(λ)` は出力および制御入力から残差への伝達関数行列です。出力および制御入力のインデックスは、整数ベクトル `Q.outputs` および `Q.controls` に含まれています。

故障検出および隔離フィルタ内部形式オブジェクト `R` は、その `i` 番目のコンポーネント `R.sys[i]` に、残差信号の `i` 番目のコンポーネント `ri` を生成するフィルタの結果の内部形式を標準状態空間形式で含み、入力-出力形式に対応します。

```
   ri = Rui(λ)*u + Rdi(λ)*d + Rfi(λ)*f + Rwi(λ)*w + Rai(λ)*aux ,
```

ここで、

```
   | Rui(λ) Rdi(λ) Rfi(λ) Rwi(λ) Rai(λ) | = |Qyi(λ) Qui(λ)|*| Gu(λ) Gd(λ) Gf(λ) Gw(λ) Ga(λ) |. 
                                                            |  I     0     0     0     0    |
```

*標準* EMMP の成分ごとの解は、`sysr.noise` と `sysr.aux` が空である場合に計算され、`Rui(λ) = Mi(λ)*Mrui(λ)`、`Rdi(λ) = Mi(λ)*Mrdi(λ)` および `Rfi(λ) = Mi(λ)*Mrfi(λ)` が保証されます。ここで、`Mi(λ)` は、`info.M` のベクトルの `i` 番目のコンポーネントに返される安定で対角的かつ可逆な更新フィルタの伝達関数行列です。このフィルタは、結果のフィルタ `Q` と `R` の `i` 番目のコンポーネントの安定性を保証するために決定されます。`sysr.noise` と `sysr.aux` の両方が空でない場合、*拡張* EMMP が成分ごとに解決され、さらに `Rwi(λ) = Mi(λ)*Mrwi(λ)` および `Rai(λ) = Mi(λ)*Mrai(λ)` が保証されます。結果のフィルタ `R.sys` の入力 `u`、`d`、`f`、`w` および `aux` のインデックスは、それぞれ整数ベクトル `R.controls`、`R.disturbances`、`R.faults`、`R.noise` および `R.aux` に含まれています。

さまざまなユーザーオプションは、キーワード引数を介して次のように指定できます。

`minimal = true`（デフォルト）の場合、最小次数フィルタ合成が実行され、`minimal = false` の場合は最小次数合成は実行されません。

`regmin = true`（デフォルト）の場合、`sysr.controls` と `sysr.disturbances` が空である場合に、最小次数の左消去器 `Nl(λ)` を選択して正則化が実行されます。`regmin = false` の場合、正則化は `Nl(λ)` を `G(λ) = [Gu(λ) Gd(λ); I 0 ]` の最小左ヌル空間基底として選択することによって実行されます。

`HDesign = H` がフル行ランクの設計行列のベクトルである場合、`H[i]*Nl(λ)` が `i` 番目のフィルタの合成に使用されます（デフォルト：`HDesign = missing`）。

`sysr.controls`、`sysr.disturbances`、`sysr.noise` および `sysr.aux` が空であり、`minimal = false` の場合、初期削減ステップが nullspace ベースのアプローチを使用して実行されます。この場合、`nullspace = true`（デフォルト）の場合、初期削減ステップで最小適切なヌル空間基底が使用され、`nullspace = false` の場合、初期削減ステップでフルオーダーのオブザーバベースのヌル空間基底が使用されます。この後者のオプションは、外乱入力のない適切なシステムにのみ使用できます。`nullspace` オプションは、`sysr.controls`、`sysr.disturbances`、`sysr.noise` または `sysr.aux` のいずれかが非空である場合、または `minimal = true` の場合は無視されます。

`simple = true` の場合、合成のための左消去器として単純な適切なヌル空間基底 `Nl(λ)` が使用されます。基底ベクトルの次数は `info.deg` に提供されます。`simple = false`（デフォルト）の場合、最小適切なヌル空間基底が計算されます。

`offset = β` は、極の安定性を評価するための境界オフセット `β` を指定します。したがって、連続時間システムの安定性のためには、すべての極の実部が最大で `-β` でなければならず、離散時間システムの安定性のためには、すべての極の絶対値が最大で `1-β` でなければなりません。`β` に使用されるデフォルト値は `sqrt(ϵ)` であり、ここで `ϵ` は作業機械精度です。

`smarg = α` は、極の安定性領域 `Cs` を定義する安定性マージンを指定します。連続時間システムの場合、`Cs` は実部が最大で `α` の複素数の集合であり、離散時間システムの場合、`Cs` は絶対値が最大で `α < 1` の複素数の集合です（すなわち、原点を中心とした半径 `α` の円の内部）。`smarg` が欠落している場合、使用されるデフォルト値は、連続時間システムの場合は `α = -β`、離散時間システムの場合は `α = 1-β` であり、ここで `β` はキーワード引数 `offset = β` で指定された境界オフセットです。

`sdeg = γ` は、フィルタ `Q` と `R` の極のための指定された安定性次数です（デフォルト：連続時間システムの極の実部に対して `γ = -0.05`、離散時間システムの極の絶対値に対して `γ = 0.95`）。

`poles = v` は、フィルタ `Q` と `R` に割り当てる安定性領域 `Cs` 内の望ましい極の複素共役セットを含む複素ベクトル `v` を指定します（デフォルト：`poles = missing`）。

`tcond = tcmax` は、使用される非直交変換の最大許容条件数 `tcmax` を指定します（デフォルト：`tcmax = 1.e4`）。

`freq = val` は、フルカラムランク（すなわち、左可逆性）解決条件をチェックするために使用されるテスト周波数の値を指定します（デフォルト：`(0,1)` の範囲でランダムに生成されます）。使用される `freq` の値は `info.freq` に返されます。

`normalize = job` は、更新行列 `Mi(λ)` の対角要素の正規化オプションを指定します。

```
  job = "gain"    – ゼロ-極-ゲイン表現のゲインでスケール（デフォルト）;
  job = "dcgain"  – DCゲインでスケール;
  job = "infnorm" – 無限ノルムの値でスケール.
```

実行された削減におけるランクの決定は、`fast = true` の場合はカラムピボッティングを伴うランクを明らかにする QR 分解に基づき、`fast = false` の場合はより信頼性の高い SVD 分解に基づきます。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ `A`、`B`、`C`、`D` の非ゼロ要素の絶対許容誤差、`E` の非ゼロ要素の絶対許容誤差、および `A`、`B`、`C`、`D` および `E` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は作業機械エプシロンで、`n` はシステム `sysf.sys` の次数です。キーワード引数 `atol3` は可観測性テストの絶対許容誤差です（デフォルト：内部で決定された値）。キーワード引数 `atol` は、同時に `atol1 = atol`、`atol2 = atol` および `atol3 = atol` を設定するために使用できます。

結果の名前付きタプル `info` には `(tcond, degs, M, freq, HDesign)` が含まれ、次のようになります。

`info.tcond` は、使用された非直交変換行列の条件数の最大値です。`info.tcond >= tcmax` の場合は警告が発行されます。

`info.degs` は、`G(λ) := [ Gu(λ) Gd(λ); I 0]` の左最小多項式ヌル空間基底の次数を増加順に含む整数ベクトルです（`G(λ)` の左クロンカーインデックスでもあります）。

`info.M` は、`i` 番目のシステム `info.M[i]` に、`i` 番目の EMMP を解決するために使用された安定で可逆な更新フィルタを含む記述子システムのベクトルです。ここで、`Mi(λ)` は対角伝達関数行列です。

`info.freq` は、左可逆性をチェックするために使用された周波数です（周波数ベースの左可逆性チェックが実行されなかった場合は `missing` に設定されます）。

`info.HDesign` は設計行列 `H` のベクトルであり、`H[i]` は故障検出フィルタ `Q` の `i` 番目のコンポーネントの合成に使用された設計行列です。`H[i]` は、設計行列が関与していない場合は空の行列です。

*メソッド:* 合成手順 EMM および EMMS が [1] を参照してコンポーネントフィルタを決定するために使用されます。手順 EMM は、[2] で提案されたモデルマッチング合成法に依存し、手順 EMMS は [3] で提案された逆ベースの方法を使用します。手順 EMM は一般的に使用されますが、強い正確な故障検出および隔離問題（強い EFDIP）が解決される場合は、手順 EMMS が使用されます。

強い EFDIP は、参照フィルタのバンク `sysr` の各コンポーネントを選択することに対応し、`Mrui(λ) = 0`、`Mrdi(λ) = 0`、`Mrfi(λ)` が可逆で、`Mrwi(λ) = 0` および `Mrai(λ) = 0` である必要があります。この場合、故障入力のインデックス `sysr.faults` のみを指定する必要があり、他の入力のインデックスは空でなければなりません。故障推定問題の解決を目指すことができ、`Mrfi(λ) = ei` を選択し、ここで `ei` は適切な単位行列の `i` 番目の行であり、結果の `info.M = 1` であることを確認します。

*参考文献:*

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques.                Springer Verlag, 2017; sec. 5.6.

[2] A. Varga, New computational approach for the design of fault       detection and isolation filters.        In M. Voicu (Ed.), "Advances in Automatic Control", vol. 754 of        The Kluwer International Series in Engineering and Computer Science,        Kluwer Academic Publishers, pp. 367-381, 2003.

[3] A. Varga. New computational paradigms in solving fault detection        and isolation problems. Annual Reviews in Control, 37:25–42, 2013. 
