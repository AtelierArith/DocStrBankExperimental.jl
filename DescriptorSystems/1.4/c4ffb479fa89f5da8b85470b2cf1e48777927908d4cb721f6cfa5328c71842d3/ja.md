```
glsol(sysg, sysf; poles = missing, sdeg = missing, mindeg = false, solgen = false, minreal = true, fast = true, 
      atol = 0, atol1 = atol, atol2 = atol, rtol, ) -> (sysx, info, sysgen)
```

記述子システム `sysg = (Ag-λEg,Bg,Cg,Dg)` と `sysf = (Af-λEf,Bf,Cf,Df)` に対して、伝達関数行列 `G(λ)` と `F(λ)` をそれぞれ持つ記述子システム `sysx` を決定します。`X(λ)` は線形有理方程式の解である伝達関数行列です。

```
X(λ)G(λ) = F(λ) .      (1)
```

`solgen = true` の場合、記述子システム `sysgen` が決定され、(1) のすべての解の生成器を表します。その伝達関数行列は次の形を持ちます：`GEN(λ) = [ X0(λ); XN(λ) ]`。任意の `X(λ)` は次のように生成できます。

```
X(λ) = X0(λ) + Z(λ)*XN(λ) ,
```

ここで `X0(λ)` は `X0(λ)G(λ) = F(λ)` を満たす特定の解、`XN(λ)` は `XN(λ)G(λ) = 0` を満たす `G(λ)` の適切な有理左零空間基底、`Z(λ)` は適切な次元を持つ任意の有理行列です。`solgen = false` の場合、`sysgen` は `nothing` に設定されます。

次の呼び出しは、

```
glsol(sysgf, pf; poles = missing, sdeg = missing, mindeg = false, solgen = false, minreal = true, fast = true, 
      atol = 0, atol1 = atol, atol2 = atol, rtol, ) -> (sysx, info, sysgen)
```

複合記述子システム `sysgf = (A-λE,B,[Cg; Cf],[Dg; Df])` を使用し、ここで `Cf` は `pf` 行を持ち、記述子システム `sysg = (A-λE,B,Cg,Dg)` と `sysf = (A-λE,B,Cf,Df)` を定義します（すなわち、`Ag-λEg = Af-λEf = A-λE` および `Bg = Bf = B`）。

生成器 `sysgen` は次のような記述子システムの実現を持ちます：`sysgen = (A0-λE0,B0, [C0; CN],[D0; DN])`。これは通常最小ではなく（観測不可能および/または非動的モードが存在）、次のようになります。

```
             ( Ai-λEi    *       *    )  
   A0-λE0  = (   0     Af-λEf    *    ) , 
             (   0       0     Al-λEl ) 

             ( *  )
       B0  = ( *  ),   ( C0 )  = ( C1 C2 C3 ) 
             ( Bl )    ( CN )    ( 0  0  Cl )
```

ここで `El`、`Ef` および `Ai` は可逆で上三角、`Ei` は nilpotent で上三角、`DN` はフル列ランクです。`A0-λE0` の対角ブロックの次元は、名前付きタプル `info` に `info.nf`、`info.ninf` および `info.nl` として返されます。

適切な基底 `XN(λ)` の最小次数記述子システムの実現は `(Al-λEl,Bl,Cl,DN)` であり、ここで `Cl` と `DN` は `pr` 列を持ち（`info.pr` に返される）、左零空間基底の次元を表します。`G(λ)` の通常のランク `nrank` は `info.nrank` に返されます。

`mindeg = false` の場合、解 `sysx` は次の形で決定されます：`sysx = (A0+F*CN-λE0,B0+F*DN,C0,D0)`。ここで行列 `F = 0` ですが、非ゼロの安定化ゲインが使用される場合、`Al+F*Bl-λEl` が安定な固有値を持つ必要があります。キーワード引数として指定されたベクトル `poles` は、固有値の希望する値を指定するために使用でき、固有値の希望する安定度 `sdeg` を強制することと共同で使用できます。`Al` の次元 `nl` は解 `X(λ)` の自由に割り当て可能な極の数であり、`info.nl` に返されます。`Af-λEf` の固有値は `G(λ)` の有限零点を含み、`Ai-λEi` の零点は `G(λ)` の無限零点を含みます。使用されたゲイン `F` のノルムは `info.fnorm` に返されます。`G(λ)` に無限零点がある場合、解 `X(λ)` は無限極を持つ可能性があります。整数ベクトル `info.rdeg` は `X(λ)` の相対行次数を含みます（すなわち、`X(λ)` の各行を適切にするために必要な積分器/遅延の数）。

`mindeg = true` の場合、最小次数の解が `X(λ) = X0(λ) + Z(λ)XN(λ)` として決定され、ここで `Z(λ)` はタイプ2の最小動的カバーに基づく次数削減を使用して決定されます。この計算には、最悪の条件数が `info.tcond` に返される非直交変換を使用することが含まれ、フィードバックおよびフィードフォワードゲインを使用し、そのノルムは `info.fnorm` に返されます。これらの量の高い値は、計算の数値安定性の潜在的な喪失を示します。

`minreal = true` の場合、計算された実現 `sysx` は最小です。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ、`Ag`、`Bg`、`Cg`、`Dg`、`Af`、`Bf`、`Cf`、`Df` の非ゼロ要素の絶対許容誤差、`Eg` および `Ef` の非ゼロ要素の絶対許容誤差、`Ag`、`Bg`、`Cg`、`Dg`、`Af`、`Bf`、`Cf`、`Df`、`Eg` および `Ef` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は作業機械のイプシロンで、`n` はシステム `sysg` と `sysf` の最大次数です。キーワード引数 `atol` は、同時に `atol1 = atol`、`atol2 = atol` を設定するために使用できます。

実行された削減におけるランクの決定は、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づき、`fast = false` の場合はより信頼性の高いSVD分解に基づきます。

*メソッド:* 有理システムを解くための[1]のメソッドの双対が使用されます。

*参考文献:*

[1] A. Varga, "Computation of least order solutions of linear rational equations",  Proc. MTNS'04, Leuven, Belgium, 2004. ```
