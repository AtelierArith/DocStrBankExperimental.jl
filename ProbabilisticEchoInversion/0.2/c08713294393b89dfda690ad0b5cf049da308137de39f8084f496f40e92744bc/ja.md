```
MCMCSolver([;sampler, parallel, nsamples, nchains; kwargs, verbose])
```

確率的バックスキャッタリングモデルをマルコフ連鎖モンテカルロを使用して反転する方法を指定して `MCMCSolver` を構築します。デフォルトでは、受け入れ率0.8のノーUターンサンプラーを使用し、1000サンプルを収集します。MCMCサンプリングのオプションについては、Turing.jlのドキュメントを参照してください。
