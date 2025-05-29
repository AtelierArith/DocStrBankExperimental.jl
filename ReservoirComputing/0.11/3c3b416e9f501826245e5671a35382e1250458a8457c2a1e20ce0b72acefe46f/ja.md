```
cycle_jumps([rng], [T], dims...; 
    cycle_weight=0.1, jump_weight=0.1, jump_size=3, return_sparse=false,
    cycle_kwargs=(), jump_kwargs=())
```

サイクルジャンプリザーバーを作成します [^Rodan2012].

# 引数

  * `rng`: ランダム数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: リザーバーマトリックス内の要素の型。デフォルトは`Float32`です。
  * `dims`: リザーバーマトリックスの次元。

# キーワード引数

  * `cycle_weight`: サイクル接続の重み。この値は単一の値または配列として提供できます。配列として提供される場合は、配列の長さが埋めたいサイクルの長さと一致することを確認してください。デフォルトは0.1です。
  * `jump_weight`: ジャンプ接続の重み。この値は単一の値または配列として提供できます。配列として提供される場合は、配列の長さが埋めたいジャンプの長さと一致することを確認してください。デフォルトは0.1です。
  * `jump_size`: ジャンプ接続間のステップ数。デフォルトは3です。
  * `return_sparse`: `sparse`マトリックスを返すためのフラグ。デフォルトは`false`です。
  * `cycle_kwargs`および`jump_kwargs`: サイクルおよびジャンプの重みのkwargsを制御する名前付きタプル。kwargsは次の通りです：

      * `sampling_type`: `weight`の負の数の分布を決定するサンプリング。`:no_sample`に設定すると符号は変更されません。`:bernoulli_sample!`に設定すると、各`weight`は`positive_prob`で設定された確率で正になります。`:irrational_sample!`に設定すると、選択された無理数の小数部分が奇数の場合、`weight`は負になります。`:regular_sample!`に設定すると、選択された`strides`の後に各重みに負の符号が割り当てられます。`strides`は単一の数または配列であることができます。デフォルトは`:no_sample`です。
      * `positive_prob`: `sampling_type`が`:bernoulli_sample!`に設定されているときの`weight`が正である確率。デフォルトは0.5です。
      * `irrational`: `weight`の符号を決定する小数を持つ無理数。デフォルトは`pi`です。
      * `start`: `irrational`の符号カウントのために小数点以下のどの位置からカウントを開始するか。デフォルトは1です。
      * `strides`: 重みに負の値を割り当てるためのストライドの数。整数または配列であることができます。デフォルトは2です。

# 例

```jldoctest
julia> res_matrix = cycle_jumps(5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.1  0.1
 0.1  0.0  0.0  0.0  0.0
 0.0  0.1  0.0  0.0  0.0
 0.1  0.0  0.1  0.0  0.0
 0.0  0.0  0.0  0.1  0.0

julia> res_matrix = cycle_jumps(5, 5; jump_size=2)
5×5 Matrix{Float32}:
 0.0  0.0  0.1  0.0  0.1
 0.1  0.0  0.0  0.0  0.0
 0.1  0.1  0.0  0.0  0.1
 0.0  0.0  0.1  0.0  0.0
 0.0  0.0  0.1  0.1  0.0
```

[^rodan2012]: Rodan, Ali, and Peter Tiňo. "Simple deterministically constructed cycle reservoirs with regular jumps." Neural computation 24.7 (2012): 1822-1852.
