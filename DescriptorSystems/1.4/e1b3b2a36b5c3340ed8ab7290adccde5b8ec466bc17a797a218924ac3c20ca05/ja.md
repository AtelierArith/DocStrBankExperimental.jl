```
grnull(sys; polynomial = false, simple = false, inner = false, fast = true, poles = missing, sdeg = missing,  
       atol = 0, atol1 = atol, atol2 = atol, rtol, offset = sqrt(ϵ) ) -> (sysrnull, info)
```

記述子システム `sys = (A-λE,B,C,D)` に対して、`p x m` 転送関数行列 `G(λ)` を持つ記述子システム `sysrnull = (Ar-λEr,Br,Cr,Dr)` を決定します。ここで、`Nr(λ)` は `G(λ)` の最小有理右零空間基であり、`G(λ)*Nr(λ) = 0` を満たします。

次の呼び出しに対して、

```
grnull(sys, p2; polynomial = false, simple = false, inner = false, fast = true, poles = missing, sdeg = missing,  
       atol = 0, atol1 = atol, atol2 = atol, rtol, offset = sqrt(ϵ) ) -> (sysrnull, info)
```

`sys` は複合システム `sys = [sys1; sys2]` を含み、`G(λ)` は `sys1` の転送関数行列であり、`G2(λ)` は `sys2` の転送関数行列です。記述子実現は `sys = (A-λE,B,[C;C2],[D;D2])` であり、`sys2` は `p2` 出力を持ちます。結果として得られる `sysrnull` は複合システム `[sysrnull1; sys2*sysrnull1] = (Ar-λEr,Br,[Cr;Cr2],[Dr;Dr2])` であり、ここで `sysrnull1 = (Ar-λEr,Br,Cr,Dr)` は転送関数行列 `Nr(λ)` を持ち、これは `G(λ)` の有理右零空間基であり、`G(λ)*Nr(λ) = 0` を満たします。また、`sys2*sysrnull1 = (Ar-λEr,Br,Cr2,Dr2)` は転送関数行列 `G2(λ)*Nr(λ)` を持ちます。

返される名前付きタプル `info` には、`info.nrank`、`info.stdim`、`info.degs`、`info.fnorm`、および `info.tcond` のコンポーネントがあります。

`polynomial = false` の場合、結果として得られる `sysrnull` は適切な転送関数行列を持ちますが、`polynomial = true` の場合、結果として得られる `sysrnull` は多項式転送関数行列を持ちます。結果として得られる基底 `Nr(λ)` には `m-r` の基底ベクトルが含まれ、ここで `r = rank G(λ)` です。ランク `r` は `info.nrank` に返されます。`simple = true` の場合、結果として得られる基底は *単純* であり、`m-r` の基底ベクトルの極の数の合計が `Nr(λ)` の極の数（すなわち、そのマクミラン次数）に等しいという条件を満たします。

非単純な適切な基底の場合、実現 `(Ar-λEr,Br,Cr,Dr)` は制御可能であり、ペンシル `[Br Ar-λEr]` は制御可能な階段形式です。完全行ランク対角ブロックの列の次元は `info.stdim` に返され、対応する右クロンネッカー指数は `info.degs` に返されます。単純な基底の場合、通常のペンシル `Ar-λEr` はブロック対角であり、`i` 番目のブロックのサイズは適切な基底の場合は `info.deg[i]`（`i` 番目の右クロンネッカー指数）であり、多項式基底の場合は `info.deg[i]+1` です。この場合、対角ブロックの次元は `info.stdim` に返され、基底ベクトルの極の増加する数は `info.degs` に返されます。`i` 番目の基底ベクトル `vi(λ)`（すなわち、`Nr(λ)` の `i` 番目の列）に対して、最小実現は `(Ari-λEri,Bri,Cr,Dr[:,i])` として明示的に構築できます。ここで、`Ari`、`Eri`、および `Bri` はそれぞれ `Ar`、`Er`、および `Br` の `i` 番目の対角ブロックであり、`Dr[:,i]` は `Dr` の `i` 番目の列です。`G2(λ)*vi(λ)` の対応する実現は `(Ari-λEri,Bri,Cr2,Dr2[:,i])` として構築でき、ここで `Dr2[:,i]` は `Dr2` の `i` 番目の列です。

適切な基底の場合、`Nr(λ)` の極は自由に割り当てることができ、ペンシル `Ar-λEr` の固有値を割り当てることができます。キーワード引数として指定されたベクトル `poles` は、望ましい固有値を指定するために使用でき、連続時間システムの場合は固有値の実部の望ましい安定度 `sdeg` を強制することと共同で使用できます。`inner = true` の場合、結果として得られる基底 `Nr(λ)` は *内側* であり、すなわち `Nr(λ)'*Nr(λ) = I` です。ここで、`Nr(s)' = transpose(Nr(-s))` は連続時間システムで `λ = s` の場合、`Nr(z)' = transpose(Nr(1/z))` は離散時間システムで `λ = z` の場合です。適切な基底が単純な場合、各結果として得られる個々の基底ベクトルは内側です。`sys2` が適切な安定領域 `Cs` の境界上に極を持ち、これが `sys1` の極でもない場合、`G2(λ)*Nr(λ)` が安定であるような内側の `Nr(λ)` は存在しません。オフセットはキーワードパラメータ `offset = β` を介して指定でき、安定領域の境界上のゼロの存在を評価するために使用されます。したがって、連続時間システムの場合、`Cs` の境界には実部が `[-β,β]` の範囲にある複素数が含まれ、離散時間システムの場合、`Cs` の境界にはモジュリが `[1-β,1+β]` の範囲にある複素数が含まれます。`β` のデフォルト値は `sqrt(ϵ)` であり、ここで `ϵ` は作業機械精度です。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ、`A`、`B`、`C`、`D` の非ゼロ要素の絶対許容誤差、`E` の非ゼロ要素の絶対許容誤差、および `A`、`B`、`C`、`D` および `E` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `ϵ` は作業機械エプシロンで、`n` はシステム `sys` の次数です。キーワード引数 `atol` は、`atol1 = atol` および `atol2 = atol` を同時に設定するために使用できます。

実行された削減におけるランクの決定は、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づいており、`fast = false` の場合はより信頼性の高いSVD分解に基づいています。単純な基底の計算には、いくつかのタイプ1最小動的カバー問題の解決が含まれます。この計算には、最悪の条件数が `info.tcond` に返される非直交変換を使用することが含まれ、フィードバックゲインを使用することが含まれ、そのノルムは `info.fnorm` に返されます。これらの量の高い値は、計算の数値安定性の潜在的な喪失を示します。

*注意:* `sysrnull` の結果として得られる実現は、`sys` の実現が最小である限り最小です。ただし、`sysrnull1` は、`sys1` の実現 (A-lambda E,B,C,D) が最小である場合にのみ最小基底です。この場合、`info.degs` は最小多項式基底のベクトルの次数、または `simple = true` の場合は結果として得られる最小単純適切基底の次数です。

*メソッド:* 最小適切な右零空間基底の計算は [1] に基づいています。最小単純適切な右零空間基底の計算には、最小適切基底から単純基底を計算するために [3] の手法が使用されます。内側の適切な右零空間基底の計算には、`Nr(λ)` の内側因子を明示的に構築するために [4] に示された式が使用されます。

*参考文献:*

[1] T.G.J. Beelen.     New algorithms for computing the Kronecker structure of a pencil      with applications to systems and control theory.      Ph. D. Thesis, Technical University Eindhoven, 1987.

[2] A. Varga.     On computing least order fault detectors using rational nullspace bases.      IFAC SAFEPROCESS'03 Symposium, Washington DC, USA, 2003.

[3] A. Varga.     On computing nullspace bases – a fault detection perspective.      Proc. IFAC 2008 World Congress, Seoul, Korea, pages 6295–6300, 2008.

[4] K. Zhou, J. C. Doyle, and K. Glover.      Robust and Optimal Control. Prentice Hall, 1996. ```
