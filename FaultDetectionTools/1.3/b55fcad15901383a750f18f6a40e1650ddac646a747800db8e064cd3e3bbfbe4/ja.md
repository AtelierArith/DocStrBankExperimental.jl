```
afdsyn(sysf::FDIModel, SFDI; rdim, nullspace = true, simple = false, minimal = true, exact = false, 
                       gamma = 1, epsreg = 0.1, sdegzer, nonstd = 1, freq, sdeg, smarg, poles, 
                       HDesign, HDesign2, scale2, FDtol, FDGainTol, FDfreq, 
                       tcond, offset, atol, atol1, atol2, atol3, rtol, fast = true)  
                       -> (Q::FDFilter, R::FDFilterIF, info)

与えられた合成モデル `sysf` と与えられたバイナリ構造ベクトル `SFDI` に対して *近似故障検出および隔離問題* (AFDIP) を解決します。計算された安定で適切なフィルタオブジェクト `Q` と `R` は、AFDIP の解を表す故障検出フィルタを含み、その内部形式をそれぞれ持ち、`R.sys[:,faults]` の伝達関数行列の `j` 番目の列が `SFDI[j] = 1` の場合に非ゼロになるように決定されます。強い AFDIP の解が実現可能な場合、`j` 番目の列は `SFDI[j] = 0` の場合にゼロになります。弱い AFDIP の解のみが実現可能な場合、`j` 番目の列は `SFDI[j] = 0` の場合に非ゼロである可能性があります。キーワードパラメータの説明については、関数 [`afdsyn`](@ref) を参照してください。
```
