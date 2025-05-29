```
 fdisspec_(sysrf::DescriptorStateSpace, freq; block = false, stabilize = false, FDGainTol = 0.01, 
                 atol, atol1, atol2, atol3, rtol, fast = true) -> (S, gains)
```

線形時間不変システム `sysrf` の伝達関数行列の強い二項構造行列 `S` を計算します（通常、故障入力から残差への伝達チャネルを表します）。`sysrf` は、`sysrf = (Af-lambda*Ef,Bf,Cf,Df)` の形の記述子システム実現を持ち、`q x mf` の伝達関数行列 `Rf(λ)` を持ちます。キーワードパラメータの説明については、[`fdisspec`](@ref) のドキュメントを参照してください。
