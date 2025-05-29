```
selfloop_feedback_cycle([rng], [T], dims...; 
    cycle_weight=0.1, selfloop_weight=0.1,
    return_sparse=false)
```

偶数ニューロンにフィードバック接続を持ち、奇数ニューロンに自己ループを持つサイクルレザーバーを作成します [^elsarraj2019]。

このアーキテクチャは、元の論文でTP2と呼ばれています。

# 方程式

$$
W_{i,j} =
\begin{cases}
    r, & \text{if } j = i - 1 \text{ for } i = 2 \dots N \\
    r, & \text{if } i = 1, j = N \\
    ll, & \text{if } i = j \text{ and } i \text{ is odd} \\
    r, & \text{if } j = i + 1 \text{ and } i \text{ is even}, i \neq N \\
    0, & \text{otherwise}
\end{cases}
$$

# 引数

  * `rng`: 乱数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: レザーバーマトリックス内の要素の型。デフォルトは`Float32`です。
  * `dims`: レザーバーマトリックスの次元。

# キーワード引数

  * `cycle_weight`: レザーバーマトリックス内のサイクル接続の重み。単一の値または配列として提供できます。配列として提供される場合は、配列の長さが埋めたいサイクルの長さと一致することを確認してください。デフォルトは0.1です。
  * `selfloop_weight`: レザーバーマトリックス内の自己ループの重み。デフォルトは0.1です。
  * `return_sparse`: `sparse`マトリックスを返すためのフラグ。デフォルトは`false`です。

# 例

```jldoctest
julia> reservoir_matrix = selfloop_feedback_cycle(5, 5)
5×5 Matrix{Float32}:
 0.1  0.1  0.0  0.0  0.1
 0.1  0.0  0.0  0.0  0.0
 0.0  0.1  0.1  0.1  0.0
 0.0  0.0  0.1  0.0  0.0
 0.0  0.0  0.0  0.1  0.1

julia> reservoir_matrix = selfloop_feedback_cycle(5, 5; self_loop_weight=0.5)
5×5 Matrix{Float32}:
 0.5  0.1  0.0  0.0  0.1
 0.1  0.0  0.0  0.0  0.0
 0.0  0.1  0.5  0.1  0.0
 0.0  0.0  0.1  0.0  0.0
 0.0  0.0  0.0  0.1  0.5
```

[^elsarraj2019]: Elsarraj, Duaa, et al. "Demystifying echo state network with deterministic simple topologies." International Journal of Computational Science and Engineering 19.3 (2019): 407-417.
