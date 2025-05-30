```
exactscorebased(X; method=:gaussian_bic, penalty=0.5, parallel=false, verbose=false)
```

与えられた観測データ `X`（列に変数がある）に対して、SilanderとMyllymäki（2006）が提案したBICスコア（または任意の分解可能スコア）を最適化するための正確なアルゴリズムを使用してCPDAGを計算します。複雑さはn*2^nであり、アルゴリズムは約20-25の変数までスケールアップする必要があります。その後、メモリが問題になります。

  * Silander, T., & Myllymäki, P. (2006). A simple approach for finding the globally optimal Bayesian network structure. In Uncertainty in Artificial Intelligence (pp. 445-452).
