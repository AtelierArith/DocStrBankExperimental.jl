```
simple_cycle([rng], [T], dims...; 
    weight=0.1, return_sparse=false,
    kwargs...)
```

単純サイクル貯水池を作成します [^rodan2010]。

# 引数

  * `rng`: 乱数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: 貯水池行列の要素の型。デフォルトは`Float32`です。
  * `dims`: 貯水池行列の次元。

# キーワード引数

  * `weight`: 貯水池行列の接続の重み。単一の値または配列として提供できます。配列として提供される場合は、配列の長さが埋めたいサイクルの長さと一致することを確認してください。デフォルトは0.1です。
  * `return_sparse`: `sparse`行列を返すためのフラグ。デフォルトは`false`です。
  * `sampling_type`: `weight`の負の数の分布を決定するサンプリング。`:no_sample`に設定すると符号は変更されません。`:bernoulli_sample!`に設定すると、各`weight`は`positive_prob`で設定された確率で正になります。`:irrational_sample!`に設定すると、選択された無理数の小数部分が奇数の場合、`weight`は負になります。`:regular_sample!`に設定すると、選択された`strides`の後に各重みに負の符号が割り当てられます。`strides`は単一の数または配列であることができます。デフォルトは`:no_sample`です。
  * `positive_prob`: `sampling_type`が`:bernoulli_sample!`に設定されているときの`weight`が正である確率。デフォルトは0.5です。
  * `irrational`: `weight`の符号を決定する小数を持つ無理数。デフォルトは`pi`です。
  * `start`: `irrational`の符号カウントのために小数点以下のどの位置からカウントを開始するか。デフォルトは1です。
  * `strides`: 重みに負の値を割り当てるためのストライドの数。整数または配列であることができます。デフォルトは2です。

# 例

```jldoctest
julia> res_matrix = simple_cycle(5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.1
 0.1  0.0  0.0  0.0  0.0
 0.0  0.1  0.0  0.0  0.0
 0.0  0.0  0.1  0.0  0.0
 0.0  0.0  0.0  0.1  0.0

julia> res_matrix = simple_cycle(5, 5; weight=11)
5×5 Matrix{Float32}:
  0.0   0.0   0.0   0.0  11.0
 11.0   0.0   0.0   0.0   0.0
  0.0  11.0   0.0   0.0   0.0
  0.0   0.0  11.0   0.0   0.0
  0.0   0.0   0.0  11.0   0.0
```

[^rodan2010]: Rodan, Ali, and Peter Tino. "Minimum complexity echo state network." IEEE transactions on neural networks 22.1 (2010): 131-144.
