```
GRUv3(in => out; return_state = false, init_kernel = glorot_uniform,
  init_recurrent_kernel = glorot_uniform, bias = true)
```

[Gated Recurrent Unit](https://arxiv.org/abs/1406.1078v3) レイヤー。RNNのように振る舞いますが、一般的にシーケンスに対してより長いメモリスパンを示します。これは、参照された論文のv3で提案されたバリアントを実装しています。

フォワードパスは次を計算します。

$$
r_t = \sigma(W_{xi} x_t + W_{hi} h_{t-1} + b_i)
z_t = \sigma(W_{xz} x_t + W_{hz} h_{t-1} + b_z)
h̃_t = \tanh(W_{xh} x_t + W_{hh̃} (r_t \odot  W_{hh} h_{t-1}) + b_h)
h_t = (1 - z_t) \odot h̃_t + z_t \odot h_{t-1}
$$

入力シーケンスのすべての `len` ステップ `t` に対して。単一のタイムステップを処理するレイヤーについては [`GRUv3Cell`](@ref) を参照してください。このレイヤーのバリアントについては [`GRU`](@ref) および [`GRUCell`](@ref) を参照してください。

`GRUv3` は [`GRU`](@ref) のより高度なバージョンではなく、単にあまり人気のないバリアントであることに注意してください。

# 引数

  * `in => out`: レイヤーの入力および出力の次元。
  * `return_state`: 出力と共に最後の状態を返すオプション。デフォルトは `false`。
  * `init_kernel`: 入力から隠れ層への接続重みの初期化関数。デフォルトは `glorot_uniform`。
  * `init_recurrent_kernel`: 隠れ層から隠れ層への接続重みの初期化関数。デフォルトは `glorot_uniform`。
  * `bias`: ゼロで初期化されたバイアス項を含めるかどうか。デフォルトは `true`。

# フォワード

```
gruv3(x, [h])
```

フォワードパスの引数は次のとおりです。

  * `x`: GRUへの入力。サイズ `in x len` の行列またはサイズ `in x len x batch_size` の配列である必要があります。
  * `h`: GRUの初期隠れ状態。サイズ `out` のベクトルまたはサイズ `out x batch_size` の行列である必要があります。提供されない場合は、[`initialstates`](@ref) によって初期化されたゼロのベクトルであると見なされます。

すべての新しい隠れ状態 `h_t` をサイズ `out x len x batch_size` の配列として返します。`return_state = true` の場合、隠れ状態 `h_t` とイテレーションの最後の状態のタプルを返します。

# 例

```julia
d_in, d_out, len, batch_size = 2, 3, 4, 5
gruv3 = GRUv3(d_in => d_out)
x = rand(Float32, (d_in, len, batch_size))
h0 = zeros(Float32, d_out)
h = gruv3(x, h0)  # out x len x batch_size
```
