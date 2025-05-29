```
minimal_init([rng], [T], dims...;
    sampling_type=:bernoulli_sample!, weight=0.1, irrational=pi,
    start=1, p=0.5)
```

`weight` によって決定される均一な重みを持つ層行列を作成します [^rodan2010]。符号の違いは選択された `sampling` によってランダムに決定されます。

# 引数

  * `rng`: 乱数生成器。デフォルトは WeightInitializers の `Utils.default_rng()` です。
  * `T`: 貯水池行列の要素の型。デフォルトは `Float32` です。
  * `dims`: 行列の次元。`res_size x in_size` に従う必要があります。

# キーワード引数

  * `weight`: 層行列を埋めるために使用される重み。デフォルトは 0.1 です。
  * `sampling_type`: `weight` の負の数の分布を決定するサンプリング。`:no_sample` に設定すると符号は変更されません。`:bernoulli_sample!` に設定すると、各 `weight` は `positive_prob` で設定された確率で正になることができます。`:irrational_sample!` に設定すると、選択された無理数の小数部分が奇数の場合、`weight` は負になります。`:regular_sample!` に設定すると、選択された `strides` の後に各重みに負の符号が割り当てられます。`strides` は単一の数または配列であることができます。デフォルトは `:no_sample` です。
  * `positive_prob`: `sampling_type` が `:bernoulli_sample!` に設定されているときの `weight` が正である確率。デフォルトは 0.5 です。
  * `irrational`: `weight` の符号を決定する小数を持つ無理数。デフォルトは `pi` です。
  * `start`: `irrational` 符号カウントの小数点以下のカウントが始まる位置。デフォルトは 1 です。
  * `strides`: 重みに負の値を割り当てるためのストライドの数。整数または配列であることができます。デフォルトは 2 です。

# 例

```jldoctest
julia> res_input = minimal_init(8, 3)
8×3 Matrix{Float32}:
  0.1  -0.1   0.1
 -0.1   0.1   0.1
 -0.1  -0.1   0.1
 -0.1  -0.1  -0.1
  0.1   0.1   0.1
 -0.1  -0.1  -0.1
 -0.1  -0.1   0.1
  0.1  -0.1   0.1

julia> res_input = minimal_init(8, 3; sampling_type=:irrational)
8×3 Matrix{Float32}:
 -0.1   0.1  -0.1
  0.1  -0.1  -0.1
  0.1   0.1  -0.1
  0.1   0.1   0.1
 -0.1  -0.1  -0.1
  0.1   0.1   0.1
  0.1   0.1  -0.1
 -0.1   0.1  -0.1

julia> res_input = minimal_init(8, 3; p=0.1) # p を下げると -> より多くの負の符号
8×3 Matrix{Float32}:
 -0.1  -0.1  -0.1
 -0.1  -0.1  -0.1
 -0.1  -0.1  -0.1
 -0.1  -0.1  -0.1
  0.1  -0.1  -0.1
 -0.1  -0.1  -0.1
 -0.1  -0.1  -0.1
 -0.1  -0.1  -0.1

julia> res_input = minimal_init(8, 3; p=0.8)# p を上げると -> より多くの正の符号
8×3 Matrix{Float32}:
  0.1   0.1  0.1
 -0.1   0.1  0.1
 -0.1   0.1  0.1
  0.1   0.1  0.1
  0.1   0.1  0.1
  0.1  -0.1  0.1
 -0.1   0.1  0.1
  0.1   0.1  0.1
```

[^rodan2010]: Rodan, Ali, and Peter Tino. "Minimum complexity echo state network." IEEE transactions on neural networks 22.1 (2010): 131-144.
