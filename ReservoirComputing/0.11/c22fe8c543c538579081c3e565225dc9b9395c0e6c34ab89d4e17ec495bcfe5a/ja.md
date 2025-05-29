```
chebyshev_mapping([rng], [T], dims...;
    amplitude=one(T), sine_divisor=one(T),
    chebyshev_parameter=one(T), return_sparse=false)
```

チェビシェフマッピングされた行列を生成します [^xie2024]。最初の行はサイン関数を使用して初期化され、その後の行はチェビシェフマッピングを介して反復的に生成されます。最初の行は次のように定義されます：

$$
    W[1, j] = \text{amplitude} \cdot \sin(j \cdot \pi / (\text{sine_divisor} 
        \cdot \text{n_cols}))
$$

j = 1, 2, …, n*cols（n*colsは通常K+1に等しく、Kは入力層ニューロンの数です）。その後の行はマッピングを適用することによって生成されます：

$$
    W[i+1, j] = \cos( \text{chebyshev_parameter} \cdot \acos(W[pi, j]))
$$

# 引数

  * `rng`: 乱数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: 貯水池行列の要素の型。デフォルトは`Float32`です。
  * `dims`: 行列の次元。`res_size x in_size`に従う必要があります。`res_size`はK+1であると仮定されます。

# キーワード引数

  * `amplitude`: 最初の行を初期化するために使用されるスケーリングファクター。このパラメータはサイン関数の振幅を調整します。デフォルト値は1です。
  * `sine_divisor`: サイン関数の位相に適用される除数。デフォルト値は1です。
  * `chebyshev_parameter`: 後続の行におけるチェビシェフマッピングの制御パラメータ。このパラメータは行列要素の分布に影響を与えます。デフォルトは1です。
  * `return_sparse`: `true`の場合、関数は行列をスパース行列として返します。デフォルトは`false`です。

# 例

```jldoctest
julia> input_matrix = chebyshev_mapping(10, 3)
10×3 Matrix{Float32}:
 0.866025  0.866025   1.22465f-16
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
```

[^xie2024]: Xie, Minzhi, Qianxue Wang, and Simin Yu. "Time Series Prediction of ESN Based on Chebyshev Mapping and Strongly Connected Topology." Neural Processing Letters 56.1 (2024): 30.
