```
lsminreal(A, E, B, C, D; fast = true, atol1 = 0, atol2, rtol, contr = true, obs = true, noseig = true) 
          -> (Ar, Er, Br, Cr, Dr, nuc, nuo, nse)
```

有理行列の線形化 `(A-λE,B,C,D)` を、次の条件を満たすように縮小形 `(Ar-λEr,Br,Cr,Dr)` に減少させます。

```
         -1                    -1
 C*(λE-A)  *B + D = Cr*(λEr-Ar)  *Br + Dr
```

`contr = true`、`obs = true`、`nseig = true` の場合、`Ar-λEr` の最小の次数 `nr` であることが求められます。このような実現は「最小」と呼ばれ、次の条件を満たします。

```
 (1) rank[Br Ar-λEr] = nr for all finite λ (有限制御可能性)

 (2) rank[Br Er] = nr (無限制御可能性)

 (3) rank[Ar-λEr; Cr] = nr for all finite λ (有限可観測性)

 (4) rank[Er; Cr] = nr (無限可観測性)

 (5) Ar-λEr has no simple infinite eigenvalues
```

条件 (1)-(4) のみを満たす実現は「不可約」と呼ばれます。

条件 (1) と (2)、条件 (3) と (4)、およびそれぞれ条件 (5) を満たすために達成された次元の削減は、`nuc`、`nuo`、`nse` に返されます。

いくつかの削減ステップは、キーワード引数 `contr`、`obs`、`nseig` を適切に選択することでスキップできます。

`contr = false` の場合、制御可能性条件 (1) と (2) は強制されません。

`obs = false` の場合、可観測性条件 (3) と (4) は強制されません。

`nseig = false` の場合、単純な無限固有値の欠如に関する条件 (5) は強制されません。

条件 (1)-(4) を強制するために、元の線形化 `(A-λE,B,C,D)` の行列に対して直交類似変換が行われ、[1] で提案されたフル行ランクペンシル [B A-λE] とフル列ランクペンシル [A-λE;C] の縮小技術の高速バージョンを使用して不可約線形化が得られます。条件 (5) を強制するために、行列の逆行列を含む残差化の公式（例えば、`[2, page 329]` を参照）を使用します。

基礎となるペンシル操作アルゴリズムは、`fast = true` の場合は列ピボットを用いたランクを明らかにするQR分解、またはSVD分解に基づくランク決定を行います。SVD分解に基づくランク決定は一般的により信頼性が高いですが、関与する計算コストは高くなります。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ行列 `A`、`B`、`C`、`D` の非ゼロ要素に対する絶対許容誤差、行列 `E` の非ゼロ要素に対する絶対許容誤差、および行列 `A`、`B`、`C`、`D` および `E` の非ゼロ要素に対する相対許容誤差を指定します。

[1] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[2] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017.  ```
