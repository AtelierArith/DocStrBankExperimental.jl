```
S = fditspec_(sysrf::DescriptorStateSpace; FDfreq = missing, block = false, poleshift = false, 
             FDtol, FDStol, atol = 0, atol1 = atol, atol2 = atol, rtol, fast = true)
```

線形時間不変システム `sysrf` の伝達関数行列 `S` の弱いまたは強い二項構造行列を計算します（通常、故障入力から残差への伝達チャネルを表します）。 `sysrf` は、形式 `sysrf = (Af-lambda*Ef,Bf,Cf,Df)` の記述子システム実現を持ち、`q x mf` の伝達関数行列 `Rf(λ)` を持ちます。 キーワードパラメータの説明については、[`fditspec`](@ref) のドキュメントを参照してください。
