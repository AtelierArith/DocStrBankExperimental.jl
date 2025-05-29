```
reverse_simple_cycle!([rng], reservoir_matrix, weight;
    sampling_type=:no_sample, irrational=pi, start=1,
    p=0.5)
```

`reservoir_matrix`に指定された`weight`で逆単純サイクルを追加します。`weight`は単一の数値または配列であることができます。

# 引数

  * `rng`: ランダム数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `reservoir_matrix`: 変更される行列。
  * `weight`: 単純サイクルとして追加される重み。単一の数値または配列のいずれかです。

# キーワード引数

  * `sampling_type`: `weight`の負の数の分布を決定するサンプリング。`:no_sample`に設定すると符号は変更されません。`:bernoulli_sample!`に設定すると、各`weight`は`positive_prob`で設定された確率で正の値になることができます。`:irrational_sample!`に設定すると、選択された無理数の小数部分が奇数の場合、`weight`は負になります。`:regular_sample!`に設定すると、選択された`strides`の後に各重みに負の符号が割り当てられます。`strides`は単一の数値または配列であることができます。デフォルトは`:no_sample`です。
  * `positive_prob`: `sampling_type`が`:bernoulli_sample!`に設定されているときの`weight`が正である確率。デフォルトは0.5です。
  * `irrational`: `weight`の符号を決定する小数部分を持つ無理数。デフォルトは`pi`です。
  * `start`: `irrational`の符号カウントのために小数点以下のどの位置からカウントを開始するか。デフォルトは1です。
  * `strides`: 重みに負の値を割り当てるためのストライドの数。整数または配列であることができます。デフォルトは2です。

# 例

```jldoctest
julia> matrix = zeros(Float32, 5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> reverse_simple_cycle!(matrix, 1.0; sampling_type=:regular_sample!)
5×5 Matrix{Float32}:
 0.0  -1.0  0.0   0.0  0.0
 0.0   0.0  1.0   0.0  0.0
 0.0   0.0  0.0  -1.0  0.0
 0.0   0.0  0.0   0.0  1.0
 1.0   0.0  0.0   0.0  0.0
```
