```
lpsminreal(A, E, B, F, C, G, D, H; fast = true, atol1 = 0, atol2, rtol, contr = true, obs = true)  
           -> (Ar, Er, Br, Fr, Cr, Gr, Dr, Hr, V, W, nuc, nuo)
```

有理行列の線形化 `(A-λE,B-λF,C-λG,D-λH)` を、適切な可逆上三角行列 `V` と `W` に対して、最小の順序 `nr` の `Ar-λEr` を持つように、縮小形 `(Ar-λEr,Br-λFr,Cr-λGr,Dr-λHr)` に還元します。

```
                  -1                                     -1
 V'*((C-λG)*(λE-A)  *(B-λF) + D-λH)*W = (Cr-λGr)*(λEr-Ar)  *(Br-λFr) + Dr-λHr
```

`contr = true` かつ `obs = true` の場合、最小の順序 `nr` の `Ar-λEr` を持つようにします。このような実現は「強最小」と呼ばれ、次の条件を満たします：

```
 (1) rank[Br-λFr Ar-λEr] = nr すべての有限および無限の λ に対して（強制御可能性）

 (2) rank[Ar-λEr; Cr-λGr] = nr すべての有限および無限の λ に対して（強観測可能性）
```

条件 (1) と (2) を満たすために達成された次元の削減は、それぞれ `nuc` と `nuo` に返されます。

`contr = true` の場合、強制御可能性条件 (1) が強制され、`W` は可逆上三角行列であるか、`nuc = 0` の場合は `W = I` です。`contr = false` の場合、強制御可能性条件 (1) は強制されず、`W = I` です。

`obs = true` の場合、強観測可能性条件 (2) が強制され、`V` は可逆上三角行列であるか、`nuo = 0` の場合は `V = I` です。`obs = false` の場合、強観測可能性条件 (2) は強制されず、`V = I` です。

条件 (1) と (2) を強制するために、元の線形化 `(A-λE,B-λF,C-λG,D-λH)` の行列に対して直交類似変換が行われ、構造化ペンシル削減アルゴリズムを使用して強最小線形化が得られます [1]。得られた実現 `(Ar-λEr,Br-λFr,Cr-λGr,Dr-λHr)` は、[2] で確立された強制御可能性および強観測可能性条件を満たします。

基礎となるペンシル操作アルゴリズムは、`fast = true` の場合は列ピボットを用いたランクを明らかにするQR分解、`fast = false` の場合はSVD分解に基づくランク決定を使用します。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算努力は高くなります。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ行列 `A`、`B`、`C`、`D` の非ゼロ要素に対する絶対許容誤差、行列 `E`、`F`、`G`、`H` の非ゼロ要素に対する絶対許容誤差、および行列 `A`、`B`、`C`、`D` と `E`、`F`、`G`、`H` の非ゼロ要素に対する相対許容誤差を指定します。

[1] F.M. Dopico, M.C. Quintana and P. Van Dooren, Linear system matrices of rational transfer functions,  to appear in "Realization and Model Reduction of Dynamical Systems", A Festschrift to honor the 70th birthday of Thanos Antoulas",  Springer-Verlag. [arXiv:1903.05016](https://arxiv.org/pdf/1903.05016.pdf)

[2] G. Verghese, Comments on ‘Properties of the system matrix of a generalized state-space system’, Int. J. Control, Vol.31(5) (1980) 1007–1009.
