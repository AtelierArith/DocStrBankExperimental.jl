MCMCのためのNo U-Turn Samplerの実装。

[ドキュメントを読む](https://tamaspapp.eu/DynamicHMC.jl/dev/)ことをお勧めします。急いでいる方のために：おそらく次のことを行いたいでしょう。

1. `LogDensityProblems`パッケージを使用して、ログ密度問題（例えばベイズ推論のため）を定義します。その後、
2. [`mcmc_with_warmup`](@ref)を使用します。
