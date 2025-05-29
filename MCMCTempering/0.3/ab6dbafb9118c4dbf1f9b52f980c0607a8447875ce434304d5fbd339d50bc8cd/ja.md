```
NonReversibleSwap <: AbstractSwapStrategy
```

各スワップステップで、この戦略は*決定論的に*まず奇数チェーンインデックスをトラバースし、隣接する要素間でスワップを提案し、次のスワップステップでは偶数チェーンインデックスをトラバースし、隣接する要素間でスワップを提案します。

このアプローチについては、彼らの論文でDEOと呼ばれている[^^SYED19]を参照してください。

[^SYED19]: Syed, S., Bouchard-Côté, Alexandre, Deligiannidis, G., & Doucet, A., Non-reversible Parallel Tempering: A Scalable Highly Parallel MCMC Scheme, arXiv:1905.02939,  (2019).
