```
 dss2ss(sys[, x0 = 0]; state-mapping = false, simple_infeigs = true, fast = true, atol1, atol2, rtol) 
           -> (sysr, xr0, Mx, Mu)
```

適切な記述子システム `sys = (A-λE,B,C,D)` と初期状態 `x0` に対して、同等の縮小次数標準システム `sysr = (Ar-λI,Br,Cr,Dr)` と対応する縮小一貫初期状態 `xr0` を返します。

`state_mapping = true` の場合、状態マッピング行列 `Mx` と `Mu` も決定され、システム `sys` と `sysr` の状態ベクトルの値 `x(t)` と `xr(t)`、および入力ベクトル `u(t)` が `x(t) = Mx*xr(t)+Mu*u(t)` のように関連付けられます。この場合、`simple_infeigs = false` であれば、高次の制御不能な無限固有値を排除できます。

デフォルトでは、`state_mapping = false` であり、`Mx = nothing` および `Mu = nothing` です。この場合、`simple_infeigs = false` であれば、高次の制御不能または観測不能な無限固有値を排除できます。

デフォルトでは、`simple_infeigs = true` であり、ペア `(A,E)` の単純無限固有値が仮定され、排除されます。

基礎となるペンシル操作アルゴリズムは、`fast = true`（デフォルト）の場合は列ピボットを用いたランクを明らかにするQR分解、または `fast = false` の場合はSVD分解に基づくランク決定を使用します。SVD分解に基づくランク決定は一般的により信頼性が高いですが、関与する計算努力は高くなります。

キーワード引数 `atol1`、`atol2` および `rtol` は、それぞれ `A`、`B`、`C`、`D` の非ゼロ要素の絶対許容誤差、`E` の非ゼロ要素の絶対許容誤差、および `A`、`B`、`C`、`D` および `E` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は正方行列 `A` と `E` の次数、`ϵ` は作業用マシンエプシロンです。
