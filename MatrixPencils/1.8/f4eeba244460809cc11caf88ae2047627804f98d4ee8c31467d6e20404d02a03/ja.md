```
lsminreal(A, B, C; fast = true, atol = 0, rtol, contr = true, obs = true, noseig = true) 
          -> (Ar, Br, Cr, nuc, nuo)
```

厳密に適切な有理行列の線形化 `(A-λI,B,C,0)` を、次の条件を満たすように縮小形 `(Ar-λI,Br,Cr,0)` に減少させます。

```
         -1                 -1
 C*(λI-A)  *B  = Cr*(λI-Ar)  *Br
```

`contr = true` および `obs = true` の場合、`Ar` の最小の次数 `nr` であることが求められます。このような実現は「最小」と呼ばれ、次の条件を満たします。

```
 (1) rank[Br Ar-λI] = nr for all λ (制御可能性);

 (2) rank[Ar-λI; Cr] = nr for all λ (可観測性).
```

条件 (1) および (2) を満たすために達成された次元の削減は、それぞれ `nuc` および `nuo` に返されます。

いくつかの削減ステップは、キーワード引数 `contr` および `obs` を適切に選択することでスキップできます。

`contr = false` の場合、制御可能性条件 (1) は強制されません。

`obs = false` の場合、可観測性条件 (2) は強制されません。

条件 (1)-(2) を強制するために、元の線形化 `(A-λI,B,C,0)` の行列に対して直交類似変換が行われ、構造化ペンシル削減アルゴリズムを使用して最小線形化が得られます。これは、[1] で提案されたフル行ランクペンシル [B A-λI] およびフル列ランクペンシル [A-λI;C] の削減技術の高速バージョンです。

基礎となるペンシル操作アルゴリズムは、`fast = true` の場合は列ピボットを用いたランクを明らかにするQR分解、またはSVD分解に基づくランク決定を使用します。SVD分解に基づくランク決定は一般的により信頼性がありますが、関与する計算コストは高くなります。

キーワード引数 `atol` および `rtol` は、それぞれ行列 `A`、`B`、`C` の非ゼロ要素に対する絶対および相対許容誤差を指定します。

[1] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981. ```
