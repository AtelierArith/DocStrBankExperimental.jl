```
GPLikelihood(obs, data, kernelfn, prior::AbstractSimulatorPrior, name=nameof(obs))
```

与えられた観測可能なデータ、データ、カーネル関数、および事前からGP尤度を構築します。カーネル関数は、`prior`からサンプリングされたパラメータに一致するパラメータを受け取り、`KernelFunctions`から任意の`Kernel`を構築する関数である必要があります。
