```
LSTMCell(in => out; init_kernel = glorot_uniform,
  init_recurrent_kernel = glorot_uniform, bias = true)
```

[長短期記憶](https://www.researchgate.net/publication/13853244_Long_Short-term_Memory)セル。RNNのように振る舞いますが、一般的にシーケンスに対してより長いメモリスパンを示します。

フォワードパスでは、次のように計算します。

$$
i_t = \sigma(W_{xi} x_t + W_{hi} h_{t-1} + b_i)
f_t = \sigma(W_{xf} x_t + W_{hf} h_{t-1} + b_f)
c_t = f_t \odot c_{t-1} + i_t \odot \tanh(W_{xc} x_t + W_{hc} h_{t-1} + b_c)
o_t = \sigma(W_{xo} x_t + W_{ho} h_{t-1} + b_o)
h_t = o_t \odot \tanh(c_t)
$$

全シーケンスを処理するレイヤーについては、[`LSTM`](@ref)も参照してください。

# 引数

  * `in => out`: レイヤーの入力および出力の次元。
  * `init_kernel`: 入力から隠れ層への接続重みの初期化関数。デフォルトは`glorot_uniform`。
  * `init_recurrent_kernel`: 隠れ層から隠れ層への接続重みの初期化関数。デフォルトは`glorot_uniform`。
  * `bias`: ゼロに初期化されたバイアス項を含めるかどうか。デフォルトは`true`。

# フォワード

```
lstmcell(x, (h, c))
lstmcell(x)
```

フォワードパスの引数は次のとおりです。

  * `x`: LSTMへの入力。サイズ`in`の行列またはサイズ`in x batch_size`の配列である必要があります。
  * `(h, c)`: LSTMの隠れ状態とセル状態を含むタプル。これらはサイズ`out`のベクトルまたはサイズ`out x batch_size`の行列である必要があります。提供されない場合は、[`initialstates`](@ref)によって初期化されたゼロのベクトルと見なされます。

タプル`(output, state)`を返します。ここで、`output = h'`は新しい隠れ状態であり、`state = (h', c')`は新しい隠れ状態とセル状態です。これらはサイズ`out`または`out x batch_size`のテンソルです。

# 例

```jldoctest
julia> l = LSTMCell(3 => 5)
LSTMCell(3 => 5)    # 180パラメータ

julia> h = zeros(Float32, 5); # 隠れ状態

julia> c = zeros(Float32, 5); # セル状態

julia> x = rand(Float32, 3, 4);  # in x batch_size

julia> y, (h′, c′) = l(x, (h, c));

julia> size(y)  # out x batch_size
(5, 4)
```
