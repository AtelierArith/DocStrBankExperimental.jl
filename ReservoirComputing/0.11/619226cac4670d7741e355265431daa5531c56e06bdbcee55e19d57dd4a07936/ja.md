```
weighted_minimal([rng], [T], dims...;
    weight=0.1, return_sparse=false,
    sampling_type=:no_sample)
```

最小の重み付き入力層行列を作成して返します。この初期化子は、[`weighted_minimal]`(@ref)と同様の構造で、等しい決定論的要素を持つ重み付き入力行列を生成します。[^lu2017]に触発されています。

この初期化子は独自の貯水池サイズを計算することに注意してください！計算された貯水池サイズが提供されたものと異なる場合、警告が表示されます。

# 引数

  * `rng`: 擬似乱数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: 貯水池行列の要素の型。デフォルトは`Float32`です。
  * `dims`: 行列の次元。`res_size x in_size`に従う必要があります。

# キーワード引数

  * `weight`: 入力行列内のすべての重みの値。デフォルトは`0.1`です。
  * `return_sparse`: `sparse`行列を返すためのフラグ。デフォルトは`false`です。
  * `sampling_type`: `weight`の負の数の分布を決定するサンプリング。`:no_sample`に設定すると符号は変更されません。`:bernoulli_sample!`に設定すると、各`weight`は`positive_prob`で設定された確率で正になります。`:irrational_sample!`に設定すると、選択された無理数の小数部分が奇数の場合、`weight`は負になります。`:regular_sample!`に設定すると、選択された`strides`の後に各重みに負の符号が割り当てられます。`strides`は単一の数または配列であることができます。デフォルトは`:no_sample`です。
  * `positive_prob`: `sampling_type`が`:bernoulli_sample!`に設定されているときの`weight`が正である確率。デフォルトは0.5です。
  * `irrational`: `weight`の符号を決定する小数部分を持つ無理数。デフォルトは`pi`です。
  * `start`: `irrational`の符号カウントのために小数点以下のどの位置からカウントを開始するか。デフォルトは1です。
  * `strides`: 重みに負の値を割り当てるためのストライドの数。整数または配列であることができます。デフォルトは2です。

# 例

```jldoctest
julia> res_input = weighted_minimal(8, 3)
┌ Warning: Reservoir size has changed!
│ 
│     Computed reservoir size (6) does not equal the provided reservoir size (8). 
│  
│     Using computed value (6). Make sure to modify the reservoir initializer accordingly. 
│ 
└ @ ReservoirComputing ~/.julia/dev/ReservoirComputing/src/esn/esn_inits.jl:159
6×3 Matrix{Float32}:
 0.1  0.0  0.0
 0.1  0.0  0.0
 0.0  0.1  0.0
 0.0  0.1  0.0
 0.0  0.0  0.1
 0.0  0.0  0.1

julia> res_input = weighted_minimal(9, 3; weight=0.99)
9×3 Matrix{Float32}:
 0.99  0.0   0.0
 0.99  0.0   0.0
 0.99  0.0   0.0
 0.0   0.99  0.0
 0.0   0.99  0.0
 0.0   0.99  0.0
 0.0   0.0   0.99
 0.0   0.0   0.99
 0.0   0.0   0.99

julia> res_input = weighted_minimal(9, 3; sampling_type=:bernoulli_sample!)
9×3 Matrix{Float32}:
  0.1  -0.0  -0.0
 -0.1  -0.0  -0.0
  0.1  -0.0   0.0
 -0.0   0.1   0.0
  0.0   0.1  -0.0
  0.0   0.1   0.0
 -0.0  -0.0  -0.1
 -0.0  -0.0   0.1
  0.0  -0.0   0.1
```

[^lu2017]: Lu, Zhixin, et al. "Reservoir observers: Model-free inference of unmeasured variables in chaotic systems." Chaos: An Interdisciplinary Journal of Nonlinear Science 27.4 (2017): 041102.
