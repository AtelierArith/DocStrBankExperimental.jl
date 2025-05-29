```
efdsyn(sysf::FDIModel, S; rdim, nullspace = true, simple = false, minimal = true, 
                       sdeg, smarg, poles, HDesign, FDtol, FDGainTol, FDfreq, 
                       tcond, offset, atol, atol1, atol2, atol3, rtol, fast = true) 
                       -> (Q::FDFilter, R::FDFilterIF, info)
```

与えられた合成モデル `sysf` と与えられたバイナリ構造ベクトル `S` に対して、*正確な故障検出および隔離問題* (EFDIP) を解決します。計算された安定で適切なフィルタオブジェクト `Q` と `R` は、EFDIP の解を表す故障検出フィルタを含み、内部形式はそれぞれ `R.sys[:,faults]` の `j` 番目の列が `S[j] = 1` の場合は非ゼロであり、`S[j] = 0` の場合はゼロになるように決定されます。キーワードパラメータの説明については、関数 [`efdsyn`](@ref) を参照してください。
