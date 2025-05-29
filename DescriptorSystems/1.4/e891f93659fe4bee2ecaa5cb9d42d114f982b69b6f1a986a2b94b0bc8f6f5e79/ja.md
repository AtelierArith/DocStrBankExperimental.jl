```
glmcover1(sys1, sys2; fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol) -> (sysx, sysy, info)
```

適切な記述子システム `sys1 = (A1-λE1,B1,C1,D1)` と `sys2 = (A2-λE2,B2,C2,D2)` に対して、伝達関数行列 `X1(λ)` と `X2(λ)` をそれぞれ使用し、タイプ1に基づく左最小動的カバーによる次数削減を行い、伝達関数行列 `X(λ)` と `Y(λ)` を持つ記述子システム `sysx` と `sysy` を次のように定義します。

```
X(λ) = X1(λ) + Y(λ)*X2(λ) ,
```

ここで `sysx` の次数は `sys1` の次数よりも小さくなります。

次の呼び出しを使用します。

```
glmcover1(sys, p1; fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol) -> (sysx, sysy, info)
```

ここで、複合記述子システム `sys = (A-λE,B,[C1; C2],[D1; D2])` を定義し、`C1` と `D1` は `p1` 行を持ち、適切な記述子システム `sys1 = (A-λE,B,C1,D1)` と `sys2 = (A-λE,B,C2,D2)` を定義します（すなわち、`A1-λE1 = A2-λE2 = A-λE` および `B1 = B2 = B`）。

結果として得られる記述子システム `sysx` と `sysy` は、次の形の可観測実現を持ちます：`sysx = (Ao-λEo,Bo1,Co,D1)` および `sysy = (Ao-λEo,Bo2,Co,0)`。ここで、ペンシル `[Ao-λEo; Co]` は（可観測性の）階段形式にあり、`νl[i] x νl[i+1]` の完全行ランク対角ブロックを持ち、`i = 1, ..., nl` に対して、`νl[nl+1] := p1` です。

結果として得られる名前付き三重項 `info` には `(stdim, tcond, fnorm)` が含まれ、`info.stdim = νl` は階段形式 `[Ao-λEo; Co]` のブロックの列の次元を含むベクトルであり、`info.tcond` は使用された非直交変換行列のフロベニウスノルム条件数の最大値であり、`info.fnorm` は次数を削減するために（内部的に）使用された出力注入ゲインのフロベニウスノルムです。`info.tcond` または `info.fnorm` の大きな値は、計算の数値安定性の喪失の可能性を示します。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ `A1`、`B1`、`C1`、`D1`、`A2`、`B2`、`C2`、`D2` の非ゼロ要素の絶対許容誤差、`E1` および `E2` の非ゼロ要素の絶対許容誤差、`A1`、`B1`、`C1`、`D1`、`A2`、`B2`、`C2`、`D2`、`E1` および `E2` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は作業機械イプシロンで、`n` はシステム `sys1` と `sys2` の最大次数です。キーワード引数 `atol` は、`atol1 = atol`、`atol2 = atol` を同時に設定するために使用できます。

実行された削減におけるランクの決定は、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づき、`fast = false` の場合はより信頼性の高いSVD分解に基づきます。

*注:* `glmcover1` は、`sys2` が適切であれば任意の記述子システム `sys1` に対しても機能します。不適切なシステム `sys1` に対しては、次数削減は `sys1` の適切な部分に対してのみ行われ、`sys1` の多項式部分は結果の実現において変更なしに含まれます。この場合、`info.stdim = νl` は `sysx` の適切な部分に対応する情報を含みます。

*メソッド:* [1] のメソッドの双対を使用して標準システムのタイプ1最小動的カバーを計算し、[2] のメソッドの双対を使用して適切な記述子システムのためのものです。結果として得られる `sysx` のマクミラン次数は、`sys2` の実現が最大制御可能である限り、達成可能な最小のものです（すなわち、ペア `(A2+F*C2-λE2,B2+F*D2)` は任意の `F` に対して制御可能です）。

*参考文献:*

[1] A. Varga, Reliable algorithms for computing minimal dynamic covers,     Proc. CDC'03, Maui, Hawaii, 2003.

[2] A. Varga. Reliable algorithms for computing minimal dynamic covers for      descriptor systems. Proc. MTNS Symposium, Leuven, Belgium, 2004.  ```
