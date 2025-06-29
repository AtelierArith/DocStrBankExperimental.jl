```
gsdec(sys; job = "finite", prescale, smarg, fast = true,  
      atol = 0,  atol1 = atol, atol2 = atol, rtol = nϵ) -> (sys1, sys2)
```

記述システム `sys = (A-λE,B,C,D)` に対して、伝達関数行列 `G(λ)` の加法的スペクトル分解 `G(λ) = G1(λ) + G2(λ)` を計算します。ここで、`G1(λ)` は記述システム `sys1 = (A1-λE1,B1,C1,D1)` の伝達関数行列であり、特定の関心領域 `Cg` の複素平面内にのみ極を持ち、`G2(λ)` は記述システム `sys2 = (A2-λE2,B2,C2,0)` の伝達関数行列であり、`Cg` の外にのみ極を持ちます。

`prescale = true` の場合、記述システムペア `(A,E)` の予備的なバランス調整が行われます。デフォルト設定は `prescale = MatrixPencils.balqual(sys.A,sys.E) > 10000` であり、ここで関数 `pbalqual` は [MatrixPencils](https://github.com/andreasvarga/MatrixPencils.jl) パッケージから、線形ペンシル `A-λE` のスケーリング品質を評価します。

キーワード引数 `smarg` が提供されている場合、`A-λE` の安定した固有値の安定性マージンを指定します。連続時間の場合、安定した固有値の実部は `smarg` 以下であり、離散時間の場合、安定した固有値の絶対値は `smarg` 以下である必要があります。`smarg = missing` の場合、使用されるデフォルト値は、連続時間システムの場合は `smarg = -sqrt(ϵ)`、離散時間システムの場合は `smarg = 1-sqrt(ϵ)` です。ここで `ϵ` は作業精度の機械精度です。

キーワード引数 `job` は、`smarg` とともに、関心領域 `Cg` を次のように定義します：

`job = "finite"` の場合、`Cg` は無限大の点を除く全複素平面であり、`sys1` は有限の極のみを持ち、`sys2` は無限の極のみを持ちます（デフォルト）。結果として得られる `A2` は非特異で上三角行列であり、結果として得られる `E2` はニルポテントで上三角行列です。

`job = "infinite"` の場合、`Cg` は無限大の点であり、`sys1` は無限の極のみを持ち、`sys2` は有限の極のみを持ち、`sys` の厳密に適切な部分です。結果として得られる `A1` は非特異で上三角行列であり、結果として得られる `E1` はニルポテントで上三角行列です。

`job = "stable"` の場合、`Cg` は `smarg` によって定義される固有値の安定性領域であり、`sys1` は安定な極のみを持ち、`sys2` は不安定な極と無限の極のみを持ちます。結果として得られるペア `(A1,E1)` と `(A2,E2)` は一般化シュール形式であり、`E1` は上三角行列で非特異であり、`E2` は上三角行列です。

`job = "unstable"` の場合、`Cg` は `smarg` によって定義される固有値の安定性領域の補集合であり、`sys1` は不安定な極と無限の極のみを持ち、`sys2` は安定な極のみを持ちます。結果として得られるペア `(A1,E1)` と `(A2,E2)` は一般化シュール形式であり、`E1` は上三角行列で、`E2` は上三角行列で非特異です。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ `A` の非ゼロ要素の絶対許容誤差、`E` の非ゼロ要素の絶対許容誤差、および `A` と `E` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は作業機械エプシロンで、`n` はシステム `sys` の次数です。キーワード引数 `atol` を使用して、同時に `atol1 = atol`、`atol2 = atol` を設定できます。

有限および無限の固有値の分離は、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づくランク決定を使用して、`fast = false` の場合はより信頼性の高いSVD分解を使用して行われます。
