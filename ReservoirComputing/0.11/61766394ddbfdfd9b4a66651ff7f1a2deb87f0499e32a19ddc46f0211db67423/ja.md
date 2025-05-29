```
true_double_cycle([rng], [T], dims...; 
    cycle_weight=0.1, second_cycle_weight=0.1,
    return_sparse=false)
```

真のダブルサイクルレザーバーを作成します。これは、[^fu2023]に触発され、[^\rodan2010]による定義に基づいてサイクルが構築されています。

# 引数

  * `rng`: ランダム数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: レザーバーマトリックス内の要素の型。デフォルトは`Float32`です。
  * `dims`: レザーバーマトリックスの次元。

# キーワード引数

  * `cycle_weight`: レザーバーマトリックス内の上部サイクル接続の重み。デフォルトは0.1です。
  * `second_cycle_weight`: レザーバーマトリックス内の下部サイクル接続の重み。デフォルトは0.1です。
  * `return_sparse`: `sparse`マトリックスを返すためのフラグ。デフォルトは`false`です。
  * `cycle_kwargs`および`second_cycle_kwargs`: 重み生成のためのkwargsを制御する名前付きタプル。kwargsは次の通りです：

      * `sampling_type`: `weight`の負の数の分布を決定するサンプリング。`:no_sample`に設定すると符号は変更されません。`:bernoulli_sample!`に設定すると、各`weight`は`positive_prob`で設定された確率で正になります。`:irrational_sample!`に設定すると、選択された無理数の小数部分が奇数の場合、`weight`は負になります。`:regular_sample!`に設定すると、選択された`strides`の後に各重みに負の符号が割り当てられます。`strides`は単一の数または配列であることができます。デフォルトは`:no_sample`です。
      * `positive_prob`: `sampling_type`が`:bernoulli_sample!`に設定されているときの`weight`が正である確率。デフォルトは0.5です。
      * `irrational`: `weight`の符号を決定する小数を持つ無理数。デフォルトは`pi`です。
      * `start`: `irrational`の符号カウントのために小数点以下のどの位置からカウントを開始するか。デフォルトは1です。
      * `strides`: 重みに負の値を割り当てるためのストライドの数。整数または配列であることができます。デフォルトは2です。

# 例

```jldoctest
julia> true_double_cycle(5, 5; cycle_weight=0.1, second_cycle_weight=0.3)
5×5 Matrix{Float32}:
 0.0  0.3  0.0  0.0  0.1
 0.1  0.0  0.3  0.0  0.0
 0.0  0.1  0.0  0.3  0.0
 0.0  0.0  0.1  0.0  0.3
 0.3  0.0  0.0  0.1  0.0
```

[^fu2023]: Fu, Jun, et al. "A double-cycle echo state network topology for time series prediction." Chaos: An Interdisciplinary Journal of Nonlinear Science 33.9 (2023).

[^rodan2010]: Rodan, Ali, and Peter Tino. "Minimum complexity echo state network." IEEE transactions on neural networks 22.1 (2010): 131-144.
