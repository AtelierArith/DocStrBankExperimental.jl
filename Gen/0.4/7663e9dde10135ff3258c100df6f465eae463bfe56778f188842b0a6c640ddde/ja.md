```
(new_trace, accepted) = hmc(
    trace, selection::Selection; L=10, eps=0.1,
    check=false, observations=EmptyChoiceMap())
```

選択されたアドレスの新しい値を提案するハミルトン・モンテカルロ（HMC）アップデートを適用し、新しいトレース（移動が受け入れられなかった場合は前のトレースと等しい）と、移動が受け入れられたかどうかを示す `Bool` を返します。

ハミルトンの方程式は、ステップサイズ `eps` で `L` ステップのリープフロッグ積分を使用して数値的に統合されます。Neal (2011) の式 (5.18)-(5.20) を参照してください。

# 参考文献

Neal, Radford M. (2011), "MCMC Using Hamiltonian Dynamics", Handbook of Markov Chain Monte Carlo, pp. 113-162. URL: http://www.mcmchandbook.net/HandbookChapter5.pdf
