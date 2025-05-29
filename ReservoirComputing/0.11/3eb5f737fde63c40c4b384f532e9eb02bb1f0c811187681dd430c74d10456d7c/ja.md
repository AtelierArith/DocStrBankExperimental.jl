```
logistic_mapping([rng], [T], dims...;
    amplitude=0.3, sine_divisor=5.9, logistic_parameter=3.7,
    return_sparse=false)
```

ロジスティックマッピングを使用して入力重み行列を生成します [^wang2022]。最初の行はサイン関数を使用して初期化されます：

$$
    W[1, j] = \text{amplitude} \cdot \sin(j \cdot \pi / 
        (\text{sine_divisor} \cdot in_size))
$$

各入力インデックス `j` に対して、`in_size` は `dims` で提供される列の数です。次の行はロジスティックマップの再帰を使用して再帰的に生成されます：

$$
    W[i+1, j] = \text{logistic_parameter} \cdot W(i, j) \cdot (1 - W[i, j])
$$

# 引数

  * `rng`: 擬似乱数生成器。デフォルトは WeightInitializers の `Utils.default_rng()` です。
  * `T`: 貯水池行列の要素の型。デフォルトは `Float32` です。
  * `dims`: 行列の次元。`res_size x in_size` に従う必要があります。

# キーワード引数

  * `amplitude`: 最初の行のサイン初期化に使用されるスケーリングパラメータ。デフォルトは 0.3 です。
  * `sine_divisor`: サイン初期化の位相を調整するために使用されるパラメータ。デフォルトは 5.9 です。
  * `logistic_parameter`: ダイナミクスを制御するロジスティックマッピング再帰のパラメータ。デフォルトは 3.7 です。
  * `return_sparse`: `true` の場合、結果の行列をスパース行列として返します。デフォルトは `false` です。

# 例

```jldoctest
julia> logistic_mapping(8, 3)
8×3 Matrix{Float32}:
 0.0529682  0.104272  0.1523
 0.185602   0.345578  0.477687
 0.559268   0.836769  0.923158
 0.912003   0.50537   0.262468
 0.296938   0.924893  0.716241
 0.772434   0.257023  0.751987
 0.650385   0.70656   0.69006
 0.841322   0.767132  0.791346

```

[^wang2022]: Wang, Heshan, et al. "Echo state network with logistic mapping and bias dropout for time series prediction." Neurocomputing 489 (2022): 196-210.
