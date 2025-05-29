```
RNNCell(in => out, σ = tanh; init_kernel = glorot_uniform, 
  init_recurrent_kernel = glorot_uniform, bias = true)
```

最も基本的な再帰層。基本的には `Dense` 層として機能しますが、出力が各タイムステップで入力にフィードバックされます。

フォワードパスでは、次の関数を実装します。

$$
h^\prime = \sigma(W_i x + W_h h + b)
$$

全体のシーケンスを処理する層については [`RNN`](@ref) を参照してください。

# 引数

  * `in => out`: 層の入力および出力の次元。
  * `σ`: 出力に適用する非線形性。デフォルトは `tanh`。
  * `init_kernel`: 入力から隠れ層への接続重みの初期化関数。デフォルトは `glorot_uniform`。
  * `init_recurrent_kernel`: 隠れ層から隠れ層への接続重みの初期化関数。デフォルトは `glorot_uniform`。
  * `bias`: ゼロで初期化されたバイアス項を含めるかどうか。デフォルトは `true`。

# フォワード

```
rnncell(x, [h])
```

フォワードパスの引数は次のとおりです。

  * `x`: RNNへの入力。サイズ `in` のベクトルまたはサイズ `in x batch_size` の行列である必要があります。
  * `h`: RNNの隠れ状態。サイズ `out` のベクトルまたはサイズ `out x batch_size` の行列である必要があります。提供されない場合は、[`initialstates`](@ref) によって初期化されたゼロのベクトルと見なされます。

タプル `(output, state)` を返します。ここで、両方の要素は更新された状態 `h'` であり、サイズ `out` または `out x batch_size` のテンソルです。

# 例

```julia
r = RNNCell(3 => 5)

# 長さ10、バッチサイズ4のシーケンス
x = [rand(Float32, 3, 4) for _ in 1:10]

# 隠れ状態を初期化
h = zeros(Float32, 5)

# 損失が全体のシーケンスに依存する場合に備えて、隠れ状態を配列 `history` に収集します。
ŷ = []

for x_t in x
  yt, h = r(x_t, h)
  ŷ = [ŷ..., yt] # ここで `push!(ŷ, h)` を使用できないのは、変異が
                 # 自動微分に優しくないためです。
                 # 代わりに `y = vcat(y, [h])` を使用できます。
end

h   # 最終的な隠れ状態
ŷ   # 各タイムステップでの隠れ状態
```
