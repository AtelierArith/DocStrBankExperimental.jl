```
grsol(sysg, sysf; poles = missing, sdeg = missing, mindeg = false, solgen = false, minreal = true, fast = true, 
      atol = 0, atol1 = atol, atol2 = atol, rtol, ) -> (sysx, info, sysgen)
```

記述子システム `sysg = (Ag-λEg,Bg,Cg,Dg)` と `sysf = (Af-λEf,Bf,Cf,Df)` に対して、伝達関数行列 `G(λ)` と `F(λ)` をそれぞれ持つ記述子システム `sysx` を決定します。`X(λ)` は線形有理方程式の解である伝達関数行列です。

```
G(λ)X(λ) = F(λ) .      (1)
```

`solgen = true` の場合、記述子システム `sysgen` が決定され、(1) のすべての解の生成器を表します。その伝達関数行列は `GEN(λ) = [ X0(λ) XN(λ) ]` の形を持ち、任意の `X(λ)` は次のように生成できます。

```
X(λ) = X0(λ) + XN(λ)*Z(λ) ,
```

ここで `X0(λ)` は `G(λ)X0(λ) = F(λ)` を満たす特定の解であり、`XN(λ)` は `G(λ)XN(λ) = 0` を満たす `G(λ)` の適切な有理右零空間基底であり、`Z(λ)` は適切な次元を持つ任意の有理行列です。`solgen = false` の場合、`sysgen` は `nothing` に設定されます。

次の呼び出しは、

```
grsol(sysgf, mf; poles = missing, sdeg = missing, mindeg = false, solgen = false, minreal = true, fast = true, 
      atol = 0, atol1 = atol, atol2 = atol, rtol, ) -> (sysx, info, sysgen)
```

複合記述子システム `sysgf = (A-λE,[Bg Bf],C,[Dg Df])` を使用し、ここで `Bf` は `mf` 列を持ち、記述子システム `sysg = (A-λE,Bg,C,Dg)` と `sysf = (A-λE,Bf,C,Df)` を定義します（すなわち、`Ag-λEg = Af-λEf = A-λE` および `Cg = Cf = C`）。

生成器 `sysgen` は、通常は最小ではない記述子システム実現 `sysgen = (A0-λE0,[B0 BN],C0,[D0 DN])` を持ち、次のようになります。

```
               ( Ar-λEr    *       *    )  
   A0-λE0    = (   0     Af-λEf    *    ) , 
               (   0       0     Ai-λEi ) 

               ( B1 | Br )
   [B0 | BN] = ( B2 | 0  ),  Cg  =   ( Cr   *    *  ) ,
               ( B3 | 0  )
```

ここで `Er`, `Ef` および `Ai` は可逆で上三角、`Ei` は nilpotent で上三角、`DN` はフル行ランクです。`A0-λE0` の対角ブロックの次元は、名前付きタプル `info` に `info.nr`, `info.nf`, および `info.ninf` として返されます。

適切な基底 `XN(λ)` の最小次数記述子システム実現は `(Ar-λEr,Br,Cr,DN)` であり、ここで `Br` と `DN` は `mr` 列を持ち（`info.mr` に返される）、右零空間基底の次元を表します。`G(λ)` の通常のランク `nrank` は `info.nrank` に返されます。

`mindeg = false` の場合、解 `sysx` は次の形で決定されます。`sysx = (A0+BN*F-λE0,B0,C0+DN*F,D0)` であり、行列 `F = 0` ですが、非ゼロの安定化ゲインが使用される場合、`Ar+Br*F-λEr` が安定な固有値を持つ必要があります。キーワード引数として指定されたベクトル `poles` は、固有値の希望する値を指定するために使用でき、固有値の希望する安定度 `sdeg` を強制することと併用できます。`Ar` の次元 `nr` は、解 `X(λ)` の自由に割り当て可能な極の数であり、`info.nr` に返されます。`Af-λEf` の固有値は `G(λ)` の有限零点を含み、`Ai-λEi` の零点は `G(λ)` の無限零点を含みます。使用されたゲイン `F` のノルムは `info.fnorm` に返されます。`G(λ)` に無限零点がある場合、解 `X(λ)` は無限極を持つ可能性があります。整数ベクトル `info.rdeg` は `X(λ)` の相対列次数を含みます（すなわち、`X(λ)` の各列を適切にするために必要な積分器/遅延の数）。

`mindeg = true` の場合、最小次数の解が `X(λ) = X0(λ) + XN(λ)*Z(λ)` として決定され、ここで `Z(λ)` はタイプ2の最小動的カバーに基づく次数削減を使用して決定されます。この計算は、最悪の条件数が `info.tcond` に返される非直交変換を使用し、フィードバックおよびフィードフォワードゲインを使用します。そのノルムは `info.fnorm` に返されます。これらの量の高い値は、計算の数値安定性の潜在的な喪失を示します。

`minreal = true` の場合、計算された実現 `sysx` は最小です。

キーワード引数 `atol1`, `atol2`, および `rtol` は、それぞれ、`Ag`, `Bg`, `Cg`, `Dg`, `Af`, `Bf`, `Cf`, `Df` の非ゼロ要素の絶対許容誤差、`Eg` および `Ef` の非ゼロ要素の絶対許容誤差、`Ag`, `Bg`, `Cg`, `Dg`, `Af`, `Bf`, `Cf`, `Df`, `Eg` および `Ef` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は作業機械のイプシロンで、`n` はシステム `sysg` と `sysf` の最大次数です。キーワード引数 `atol` は、同時に `atol1 = atol`, `atol2 = atol` を設定するために使用できます。

実行された削減におけるランクの決定は、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づき、`fast = false` の場合はより信頼性の高いSVD分解に基づきます。

*メソッド:* 有理システムを解くために [1] の方法が使用されます。

*参考文献:*

[1] A. Varga, "Computation of least order solutions of linear rational equations",  Proc. MTNS'04, Leuven, Belgium, 2004. ```
