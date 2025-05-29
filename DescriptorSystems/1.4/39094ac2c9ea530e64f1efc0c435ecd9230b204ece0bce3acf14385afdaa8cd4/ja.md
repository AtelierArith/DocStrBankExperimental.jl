```
sysr = gminreal(sys; contr = true, obs = true, noseig = true, prescale, fast = true, 
                atol = 0, atol1 = atol, atol2 = atol, rtol = nϵ)
```

記述子システム `sys = (A-λE,B,C,D)` の次数 `n` に対して、次数 `nr ≤ n` の縮小次数記述子システム `sysr = (Ar-λEr,Br,Cr,Dr)` を計算します。`sys` と `sysr` は同じ伝達関数行列を持つ、すなわち、

```
         -1                    -1
 C*(λE-A)  *B + D = Cr*(λEr-Ar)  *Br + Dr .
```

`prescale = true` の場合、記述子システム行列の事前バランスが実行されます。デフォルト設定は `prescale = gbalqual(sys) > 10000` であり、ここで `gbalqual(sys)` は記述子システムモデル `sys` のスケーリング品質です（[`gbalqual`](@ref) を参照）。

最小の次数 `nr` は、`contr = true`、`obs = true`、`nseig = true` の場合に達成されます。このような実現は `minimal` と呼ばれ、次の条件を満たします：

```
 (1) rank[Br Ar-λEr] = nr for all finite λ (有限制御可能性)

 (2) rank[Br Er] = nr (無限制御可能性)

 (3) rank[Ar-λEr; Cr] = nr for all finite λ (有限可観測性)

 (4) rank[Er; Cr] = nr (無限可観測性)

 (5) Ar-λEr は単純な無限固有値を持たない
```

条件 (1)-(4) のみを満たす実現は `irreducible` と呼ばれます。

いくつかの削減ステップは、キーワード引数 `contr`、`obs`、`nseig` を適切に選択することでスキップできます。

`contr = false` の場合、制御可能性条件 (1) および (2) は強制されません。

`obs = false` の場合、可観測性条件 (3) および (4) は強制されません。

`nseig = false` の場合、単純な無限固有値の欠如に関する条件 (5) は強制されません。

条件 (1)-(4) を強制するために、元の実現 `(A-λE,B,C,D)` の行列に対して直交類似変換が実行され、構造化ペンシル削減アルゴリズムを使用して不可約実現が得られます。これは、[B A-λE] のフル行ランクペンシルおよび [A-λE;C] のフル列ランクペンシルの削減技術の高速バージョンに基づいています [1]。条件 (5) を強制するために、残差化式（例えば、`[2, page 329]` を参照）が使用され、行列の逆行列計算が含まれます。

基礎となるペンシル操作アルゴリズムは、`fast = true` の場合は列ピボットを用いたランクを明らかにするQR分解、またはSVD分解に基づくランク決定を使用します。SVD分解に基づくランク決定は一般的により信頼性が高いですが、関与する計算コストは高くなります。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ行列 `A`、`B`、`C`、`D` の非ゼロ要素に対する絶対許容誤差、行列 `E` の非ゼロ要素に対する絶対許容誤差、行列 `A`、`B`、`C`、`D` および `E` の非ゼロ要素に対する相対許容誤差を指定します。デフォルトの相対許容誤差は `nϵ` であり、ここで `ϵ` は作業用 *マシンエプシロン* で、`n` はシステム `sys` の次数です。キーワード引数 `atol` を使用すると、`atol1 = atol` および `atol2 = atol` を同時に設定できます。

[1] P. Van Dooreen, The generalized eigenstructure problem in linear system theory,  IEEE Transactions on Automatic Control, vol. AC-26, pp. 111-129, 1981.

[2] A. Varga, Solving Fault Diagnosis Problems - Linear Synthesis Techniques, Springer Verlag, 2017.  ```
