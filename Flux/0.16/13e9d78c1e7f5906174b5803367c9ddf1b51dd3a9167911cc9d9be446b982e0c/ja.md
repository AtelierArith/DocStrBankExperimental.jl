```
RNN(in => out, σ = tanh; return_state = false,
  init_kernel = glorot_uniform, init_recurrent_kernel = glorot_uniform, bias = true)
```

最も基本的な再帰層です。基本的には `Dense` 層として機能しますが、出力が各タイムステップで入力にフィードバックされます。

フォワードパスでは次を計算します。

$$
h_t = \sigma(W_i x_t + W_h h_{t-1} + b)
$$

入力シーケンスのすべての `len` ステップ `t` に対して。

単一のタイムステップを処理する層については [`RNNCell`](@ref) を参照してください。

# 引数

  * `in => out`: 層の入力および出力の次元。
  * `σ`: 出力に適用する非線形性。デフォルトは `tanh`。
  * `return_state`: 出力と共に最後の状態を返すオプション。デフォルトは `false`。
  * `init_kernel`: 入力から隠れ層への接続重みの初期化関数。デフォルトは `glorot_uniform`。
  * `init_recurrent_kernel`: 隠れ層から隠れ層への接続重みの初期化関数。デフォルトは `glorot_uniform`。
  * `bias`: ゼロで初期化されたバイアス項を含めるかどうか。デフォルトは `true`。

# フォワード

```
rnn(x, [h])
```

フォワードパスの引数は次の通りです。

  * `x`: RNNへの入力。サイズは `in x len` の行列またはサイズ `in x len x batch_size` の配列である必要があります。
  * `h`: RNNの初期隠れ状態。与えられた場合、サイズ `out` のベクトルまたはサイズ `out x batch_size` の行列です。提供されない場合は、[`initialstates`](@ref) によって初期化されたゼロのベクトルと見なされます。

すべての新しい隠れ状態 `h_t` をサイズ `out x len x batch_size` の配列として返します。`return_state = true` の場合、隠れ状態 `h_t` とイテレーションの最後の状態のタプルを返します。

# 例

```jldoctest
julia> d_in, d_out, len, batch_size = 4, 6, 3, 5;

julia> x = rand(Float32, (d_in, len, batch_size));

julia> h = zeros(Float32, (d_out, batch_size));

julia> rnn = RNN(d_in => d_out)
RNN(4 => 6, tanh)   # 66 パラメータ

julia> y = rnn(x, h);   # [y] = [d_out, len, batch_size]
```

時には、初期隠れ状態が学習可能なパラメータであることがあります。この場合、`RNN` はカスタム構造体でラップする必要があります。

```julia
struct Model
  rnn::RNN
  h0::AbstractVector
end

Flux.@layer Model

(m::Model)(x) = m.rnn(x, m.h0)

model = Model(RNN(32 => 64), zeros(Float32, 64))
```
