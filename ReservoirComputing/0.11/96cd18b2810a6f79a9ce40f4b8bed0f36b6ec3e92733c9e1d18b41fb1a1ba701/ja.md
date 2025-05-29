```
selfloop_cycle([rng], [T], dims...; 
    cycle_weight=0.1, selfloop_weight=0.1,
    return_sparse=false, kwargs...)
```

自己ループを追加したシンプルなサイクルリザーバを作成します [^elsarraj2019]。

このアーキテクチャは、元の論文ではTP1と呼ばれています。

# 方程式

$$
W_{i,j} =
\begin{cases}
    ll, & \text{if } i = j \\
    r, & \text{if } j = i - 1 \text{ for } i = 2 \dots N \\
    r, & \text{if } i = 1, j = N \\
    0, & \text{otherwise}
\end{cases}
$$

# 引数

  * `rng`: ランダム数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: リザーバ行列の要素の型。デフォルトは`Float32`です。
  * `dims`: リザーバ行列の次元。

# キーワード引数

  * `cycle_weight`: リザーバ行列のサイクル接続の重み。単一の値または配列として提供できます。配列として提供される場合は、配列の長さが埋めたいサイクルの長さと一致することを確認してください。デフォルトは0.1です。
  * `selfloop_weight`: リザーバ行列の自己ループの重み。単一の値または配列として提供できます。配列として提供される場合は、配列の長さが埋めたい対角線の長さと一致することを確認してください。デフォルトは0.1です。
  * `return_sparse`: `sparse`行列を返すためのフラグ。デフォルトは`false`です。
  * `sampling_type`: `weight`の負の数の分布を決定するサンプリング。`:no_sample`に設定すると符号は変更されません。`:bernoulli_sample!`に設定すると、各`weight`は`positive_prob`で設定された確率で正になります。`:irrational_sample!`に設定すると、選択された無理数の小数部分が奇数の場合、`weight`は負になります。`:regular_sample!`に設定すると、選択された`strides`の後に各重みに負の符号が割り当てられます。`strides`は単一の数または配列であることができます。デフォルトは`:no_sample`です。
  * `positive_prob`: `sampling_type`が`:bernoulli_sample!`に設定されているときの`weight`が正である確率。デフォルトは0.5です。
  * `irrational`: `weight`の符号を決定する小数を持つ無理数。デフォルトは`pi`です。
  * `start`: `irrational`の符号カウントのために小数点以下のどの位置からカウントを開始するか。デフォルトは1です。
  * `strides`: 重みに負の値を割り当てるためのストライドの数。整数または配列であることができます。デフォルトは2です。

# 例

```jldoctest
julia> reservoir_matrix = selfloop_cycle(5, 5)
5×5 Matrix{Float32}:
 0.1  0.0  0.0  0.0  0.1
 0.1  0.1  0.0  0.0  0.0
 0.0  0.1  0.1  0.0  0.0
 0.0  0.0  0.1  0.1  0.0
 0.0  0.0  0.0  0.1  0.1

julia> reservoir_matrix = selfloop_cycle(5, 5; weight=0.2, selfloop_weight=0.5)
5×5 Matrix{Float32}:
 0.5  0.0  0.0  0.0  0.2
 0.2  0.5  0.0  0.0  0.0
 0.0  0.2  0.5  0.0  0.0
 0.0  0.0  0.2  0.5  0.0
 0.0  0.0  0.0  0.2  0.5
```

[^elsarraj2019]: Elsarraj, Duaa, et al. "Demystifying echo state network with deterministic simple topologies." International Journal of Computational Science and Engineering 19.3 (2019): 407-417.
