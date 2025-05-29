```
sysr = gir(sys; finite = true, infinite = true, contr = true, obs = true, noseig = false,
           fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol = nϵ)
```

次のような次数 `n` の記述子システム `sys = (A-λE,B,C,D)` に対して、同じ伝達関数行列を持つ次数 `nr ≤ n` の縮小次数記述子システム `sysr = (Ar-λEr,Br,Cr,Dr)` を計算します。すなわち、

```
         -1                    -1
 C*(λE-A)  *B + D = Cr*(λEr-Ar)  *Br + Dr .
```

最小の次数 `nr` は、`finite = true`、`infinite = true`、`contr = true`、`obs = true`、および `nseig = true` の場合に達成されます。このような実現は「最小」と呼ばれ、次の条件を満たします：

```
 (1) rank[Br Ar-λEr] = nr すべての有限 λ に対して（有限制御可能性）

 (2) rank[Br Er] = nr （無限制御可能性）

 (3) rank[Ar-λEr; Cr] = nr すべての有限 λ に対して（有限可観測性）

 (4) rank[Er; Cr] = nr （無限可観測性）

 (5) Ar-λEr は単純な無限固有値を持たない
```

条件 (1)-(4) のみを満たす実現は「不可約」と呼ばれ、デフォルトで計算されます。

いくつかの削減ステップは、キーワード引数 `contr`、`obs`、`finite`、`infinite`、および `nseig` を適切に選択することでスキップできます。

`contr = false` の場合、制御可能性条件 (1) および (2) は強制されません。`contr = true` かつ `finite = true` の場合、有限制御可能性条件 (1) が強制されます。`contr = true` かつ `finite = false` の場合、有限制御可能性条件 (1) は強制されません。`contr = true` かつ `infinite = true` の場合、無限制御可能性条件 (2) が強制されます。`contr = true` かつ `infinite = false` の場合、無限制御可能性条件 (2) は強制されません。

`obs = false` の場合、可観測性条件 (3) および (4) は強制されません。`obs = true` かつ `finite = true` の場合、有限可観測性条件 (3) が強制されます。`obs = true` かつ `finite = false` の場合、有限可観測性条件 (3) は強制されません。`obs = true` かつ `infinite = true` の場合、無限可観測性条件 (4) が強制されます。`obs = true` かつ `infinite = false` の場合、無限可観測性条件 (4) は強制されません。

`nseig = true` の場合、単純な無限固有値が存在しないという条件 (5) も強制されます。

条件 (1)-(4) を強制するために、`[1, page 328]` の「手続き GIR」が使用され、元の実現 `(A-λE,B,C,D)` の行列に対して直交類似変換を行い、構造化ペンシル削減アルゴリズムを使用して不可約実現を取得します。条件 (5) を強制するために、残差化公式（例えば、`[1, page 329]` を参照）を使用し、行列の逆行列を含む操作が行われます。

基礎となるペンシル操作アルゴリズムは、`fast = true` の場合は列ピボットを用いたランクを明らかにするQR分解、またはSVD分解に基づくランク決定を行います。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算コストは高くなります。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ行列 `A`、`B`、`C`、`D` の非ゼロ要素に対する絶対許容誤差、行列 `E` の非ゼロ要素に対する絶対許容誤差、および行列 `A`、`B`、`C`、`D` および `E` の非ゼロ要素に対する相対許容誤差を指定します。デフォルトの相対許容誤差は `nϵ` であり、ここで `ϵ` は作業用 *マシンイプシロン* で、`n` はシステム `sys` の次数です。キーワード引数 `atol` を使用すると、`atol1 = atol` および `atol2 = atol` を同時に設定できます。

[1] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017.  ```
