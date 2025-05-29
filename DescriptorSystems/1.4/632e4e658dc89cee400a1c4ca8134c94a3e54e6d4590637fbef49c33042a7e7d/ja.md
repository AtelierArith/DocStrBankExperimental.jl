```
grmcover2(sys1, sys2; fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol) -> (sysx, sysy, info)
```

適切な記述子システム `sys1 = (A1-λE1,B1,C1,D1)` と `sys2 = (A2-λE2,B2,C2,D2)` に対して、伝達関数行列 `X1(λ)` と `X2(λ)` をそれぞれ使用し、タイプ2に基づく右最小動的カバーによる次数削減を行い、伝達関数行列 `X(λ)` と `Y(λ)` を持つ記述子システム `sysx` と `sysy` を求めます。これにより、次の関係が成り立ちます。

```
X(λ) = X1(λ) + X2(λ)*Y(λ) ,
```

そして `sysx` の次数は `sys1` の次数よりも小さくなります。

次の呼び出しを行うと、

```
grmcover2(sys, m1; fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol) -> (sysx, sysy, info)
```

複合記述子システム `sys = (A-λE,[B1 B2],C,[D1 D2])` を使用し、ここで `B1` と `D1` は `m1` 列を持ち、適切な記述子システム `sys1 = (A-λE,B1,C,D1)` と `sys2 = (A-λE,B2,C,D2)` を定義します（すなわち、`A1-λE1 = A2-λE2 =: A-λE` および `C1 = C2 =: C`）。

結果として得られる記述子システム `sysx` と `sysy` は、次の形の制御可能な実現を持ちます：`sysx = (Ar-λEr,Br,Cr1,Dr1)` および `sysy = (Ar-λEr,Br,Cr2,Dr2)`。ここで、ペンシル `[Br Ar-λEr]` は（制御可能性の）階段形式であり、`νr[i] x νr[i-1]` のフル行ランク対角ブロックを持ち、`i = 1, ..., nr` の範囲で、`νr[0] := m1` です。

結果として得られる名前付き三重項 `info` には `(stdim, tcond, fnorm, gnorm)` が含まれます。ここで `info.stdim = νr` は階段形式 `[Br Ar-λEr]` のブロックの行次元を含むベクトルであり、`info.tcond` は使用された非直交変換行列のフロベニウスノルム条件数の最大値、`info.fnorm` は次数削減のために使用された（内部的に）状態フィードバックゲインのフロベニウスノルム、`info.gnorm` は次数削減のために使用された（内部的に）フィードフォワードゲインのフロベニウスノルムです。`info.tcond`、`info.fnorm`、または `info.gnorm` の大きな値は、計算の数値安定性の喪失の可能性を示します。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ `A1`、`B1`、`C1`、`D1`、`A2`、`B2`、`C2`、`D2` の非ゼロ要素の絶対許容誤差、`E1` および `E2` の非ゼロ要素の絶対許容誤差、`A1`、`B1`、`C1`、`D1`、`A2`、`B2`、`C2`、`D2`、`E1` および `E2` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は作業機械エプシロンで、`n` はシステム `sys1` と `sys2` の最大次数です。キーワード引数 `atol` は、`atol1 = atol`、`atol2 = atol` を同時に設定するために使用できます。

実行された削減におけるランクの決定は、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づき、`fast = false` の場合はより信頼性の高いSVD分解に基づきます。

*注意:* `grmcover2` は、`sys2` が適切である場合、任意の記述子システム `sys1` に対しても機能します。不適切なシステム `sys1` に対しては、次数削減は `sys1` の適切な部分に対してのみ行われ、`sys1` の多項式部分は結果の実現に変更なしで含まれます。この場合、`info.stdim = νr` は `sysx` の適切な部分に対応する情報を含みます。

*方法:* [1] の方法を使用して標準システムのタイプ2最小動的カバーを計算し、[2] の方法を使用して適切な記述子システムのための最小動的カバーを計算します。結果として得られる `sysx` のマクミラン次数は、`sys2` の実現が最大観測可能である限り、達成可能な最小のものです（すなわち、ペア `(A2+B2*F-λE2,C2+D2*F)` は任意の `F` に対して観測可能です）。

参考文献:

[1] A. Varga, Reliable algorithms for computing minimal dynamic covers,     Proc. CDC'03, Maui, Hawaii, 2003.

[2] A. Varga. Reliable algorithms for computing minimal dynamic covers for      descriptor systems. Proc. MTNS Symposium, Leuven, Belgium, 2004.  ```
