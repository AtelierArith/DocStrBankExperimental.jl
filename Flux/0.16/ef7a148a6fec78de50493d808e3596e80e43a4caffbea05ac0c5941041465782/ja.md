```
LSTM(in => out; return_state = false, init_kernel = glorot_uniform,
  init_recurrent_kernel = glorot_uniform, bias = true)
```

[長短期記憶](https://www.researchgate.net/publication/13853244_Long_Short-term_Memory) 再帰層。RNNのように振る舞いますが、一般的にシーケンスに対してより長い記憶期間を示します。

内部の良い概要については[この記事](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)を参照してください。

フォワードパスでは、次を計算します。

$$
i_t = \sigma(W_{xi} x_t + W_{hi} h_{t-1} + b_i)
f_t = \sigma(W_{xf} x_t + W_{hf} h_{t-1} + b_f)
c_t = f_t \odot c_{t-1} + i_t \odot \tanh(W_{xc} x_t + W_{hc} h_{t-1} + b_c)
o_t = \sigma(W_{xo} x_t + W_{ho} h_{t-1} + b_o)
h_t = o_t \odot \tanh(c_t)
$$

入力シーケンスのすべての `len` ステップ `t` に対して。単一のタイムステップを処理するレイヤーについては[`LSTMCell`](@ref)を参照してください。

# 引数

  * `in => out`: レイヤーの入力および出力の次元。
  * `return_state`: 出力と共に最後の状態を返すオプション。デフォルトは `false`。
  * `init_kernel`: 入力から隠れ層への接続重みの初期化関数。デフォルトは `glorot_uniform`。
  * `init_recurrent_kernel`: 隠れ層から隠れ層への接続重みの初期化関数。デフォルトは `glorot_uniform`。
  * `bias`: ゼロで初期化されたバイアス項を含めるかどうか。デフォルトは `true`。

# フォワード

```
lstm(x, (h, c))
lstm(x)
```

フォワードパスの引数は次のとおりです。

  * `x`: LSTMへの入力。サイズ `in x len` の行列またはサイズ `in x len x batch_size` の配列である必要があります。
  * `(h, c)`: LSTMの隠れ状態とセル状態を含むタプル。サイズ `out` のベクトルまたはサイズ `out x batch_size` の行列である必要があります。提供されない場合は、[`initialstates`](@ref) によって初期化されたゼロのベクトルと見なされます。

すべての新しい隠れ状態 `h_t` をサイズ `out x len` または `out x len x batch_size` の配列として返します。`return_state = true` の場合、隠れ状態 `h_t` とイテレーションの最後の状態のタプルを返します。

# 例

```julia
struct Model
  lstm::LSTM
  h0::AbstractVector # 学習可能な初期隠れ状態
  c0::AbstractVector
end

Flux.@layer Model

(m::Model)(x) = m.lstm(x, (m.h0, m.c0))

d_in, d_out, len, batch_size = 2, 3, 4, 5
x = rand(Float32, (d_in, len, batch_size))
model = Model(LSTM(d_in => d_out), zeros(Float32, d_out), zeros(Float32, d_out))
h = model(x)
size(h)  # out x len x batch_size
```
