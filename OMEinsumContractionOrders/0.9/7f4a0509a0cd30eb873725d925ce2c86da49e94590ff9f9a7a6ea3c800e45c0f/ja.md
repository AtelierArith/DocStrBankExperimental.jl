```
TreeSA{RT,IT,GM}
TreeSA(; sc_target=20, βs=collect(0.01:0.05:15), ntrials=10, niters=50,
    sc_weight=1.0, rw_weight=0.2, initializer=:greedy, greedy_config=GreedyMethod(; nrepeat=1))
```

テンソル式ツリー上でのシミュレーテッドアニーリングを使用して、einsum収束パターンを最適化します。

  * `sc_target` は目標の空間複雑性です。
  * `ntrials`、`βs`、および `niters` はアニーリングパラメータであり、`ntrials` 回の独立したアニーリングを行い、それぞれのアニーリングには `βs` で指定された逆温度があります。各温度で、ツリーの `niters` 回の更新を行います。
  * `sc_weight` は、時間の複雑性に対する損失における空間の複雑性の相対的重要性係数です。
  * `rw_weight` は、時間の複雑性に対する損失におけるメモリの読み書きの相対的重要性係数です。
  * `initializer` は初期構成を決定する方法を指定し、`:greedy` または `:random` にすることができます。初期構成を生成するために `:greedy` メソッドを使用する場合、`greedy_method` と `greedy_nrepeat` の2つの追加引数も使用します。
  * `nslices` はスライスされた脚の数で、デフォルトは0です。
  * `fixed_slices` はスライスされた脚のベクトルで、デフォルトは `[]` です。

### 参考文献

  * [Recursive Multi-Tensor Contraction for XEB Verification of Quantum Circuits](https://arxiv.org/abs/2108.05665)
