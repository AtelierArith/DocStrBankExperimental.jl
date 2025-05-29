```
sample(bpc::CuBitsProbCircuit, num_samples::Int, num_rand_vars::Int, types; rng=default_rng())
```

条件なしで回路の同時分布から`num_samples`を生成します。サンプルはGPU上で生成されます。

  * `bpc`: GPU上の回路 (CuBitProbCircuit)
  * `num_samples`: 生成するサンプルの数
  * `num_rand_vars`: 回路内のランダム変数の数
  * `types`: 可能な入力タイプの配列
  * `rng`: (オプション) ランダム数生成器

返される配列のサイズは`(num_samples, 1, size(data, 2))`です。
