```
delay_line_backward([rng], [T], dims...;
    weight=0.1, fb_weight=0.2, return_sparse=false,
    delay_kwargs=(), fb_kwargs=())
```

指定された `dims` と重みを持つ遅延ラインバックワードリザーバを作成します。バックワード接続を持つ行列を作成します [^rodan2010] に記載されているように。

# 引数

  * `rng`: ランダム数生成器。デフォルトは WeightInitializers の `Utils.default_rng()` です。
  * `T`: リザーバ行列の要素の型。デフォルトは `Float32` です。
  * `dims`: リザーバ行列の次元。

# キーワード引数

  * `weight`: 重みはリザーバ内の前方接続の絶対値を決定します。これは単一の値または配列として提供できます。配列として提供される場合は、配列の長さが埋めたい下対角線の長さと一致することを確認してください。デフォルトは 0.1 です。
  * `fb_weight`: リザーバ内のバックワード接続の絶対値を決定します。これは単一の値または配列として提供できます。配列として提供される場合は、配列の長さが埋めたい下対角線の長さと一致することを確認してください。デフォルトは 0.2 です。
  * `fb_shift`: バックワード接続が対角線からどれだけ離れるか。デフォルトは 2 です。
  * `return_sparse`: `sparse` 行列を返すためのフラグ。デフォルトは `false` です。
  * `delay_kwargs` と `fb_kwargs`: 遅延ラインの重みとフィードバック重みのためのキーワード引数を制御する名前付きタプルです。キーワード引数は次のとおりです：

      * `sampling_type`: `weight` の負の数の分布を決定するサンプリング。`:no_sample` に設定すると符号は変更されません。`:bernoulli_sample!` に設定すると、各 `weight` は `positive_prob` で設定された確率で正になります。`:irrational_sample!` に設定すると、選択された無理数の小数部分が奇数の場合、`weight` は負になります。`:regular_sample!` に設定すると、選択された `strides` の後に各重みに負の符号が割り当てられます。`strides` は単一の数または配列であることができます。デフォルトは `:no_sample` です。
      * `positive_prob`: `sampling_type` が `:bernoulli_sample!` に設定されているときの `weight` が正である確率。デフォルトは 0.5 です。
      * `irrational`: `weight` の符号を決定する小数を持つ無理数。デフォルトは `pi` です。
      * `start`: `irrational` 符号カウントの小数点以下のどの位置からカウントを開始するか。デフォルトは 1 です。
      * `strides`: 重みに負の値を割り当てるためのストライドの数。整数または配列であることができます。デフォルトは 2 です。

# 例

```jldoctest
julia> res_matrix = delay_line_backward(5, 5)
5×5 Matrix{Float32}:
 0.0  0.2  0.0  0.0  0.0
 0.1  0.0  0.2  0.0  0.0
 0.0  0.1  0.0  0.2  0.0
 0.0  0.0  0.1  0.0  0.2
 0.0  0.0  0.0  0.1  0.0

julia> res_matrix = delay_line_backward(Float16, 5, 5)
5×5 Matrix{Float16}:
 0.0  0.2  0.0  0.0  0.0
 0.1  0.0  0.2  0.0  0.0
 0.0  0.1  0.0  0.2  0.0
 0.0  0.0  0.1  0.0  0.2
 0.0  0.0  0.0  0.1  0.0
```

[^rodan2010]: Rodan, Ali, and Peter Tino. "Minimum complexity echo state network." IEEE transactions on neural networks 22.1 (2010): 131-144.
