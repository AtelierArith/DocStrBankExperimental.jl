```
sample(bpc::CuBitsProbCircuit, num_samples, data::CuMatrix; rng=default_rng())
```

`data`の各データポイントに対して、データに条件付けられた回路の結合分布から`num_samples`を生成します。サンプルはGPUを使用して生成されます。

  * `bpc`: GPU上の回路 (CuBitProbCircuit)
  * `num_samples`: 生成するサンプルの数
  * `rng`: (オプション) 擬似乱数生成器

返されるCuArrayのサイズは`(num_samples, size(data, 1), size(data, 2))`です。
