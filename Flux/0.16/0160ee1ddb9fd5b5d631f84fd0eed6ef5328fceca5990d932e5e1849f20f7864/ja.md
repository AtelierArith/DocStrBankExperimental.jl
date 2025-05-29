```
GRUCell(in => out; init_kernel = glorot_uniform,
  init_recurrent_kernel = glorot_uniform, bias = true)
```

[Gated Recurrent Unit](https://arxiv.org/abs/1406.1078v1) レイヤー。RNNのように振る舞いますが、一般的にシーケンスに対してより長いメモリスパンを示します。これは、参照された論文のv1で提案されたバリアントを実装しています。

フォワードパスでは、次を計算します。

$$
r = \sigma(W_{xi} x + W_{hi} h + b_i)
z = \sigma(W_{xz} x + W_{hz} h + b_z)
h̃ = \tanh(W_{xh} x + r \odot W_{hh} h + b_h)
h' = (1 - z) \odot h̃ + z \odot h
$$

全シーケンスを処理するレイヤーについては、[`GRU`](@ref)も参照してください。

# 引数

  * `in => out`: レイヤーの入力および出力の次元。
  * `init_kernel`: 入力から隠れ層への接続重みの初期化関数。デフォルトは `glorot_uniform`。
  * `init_recurrent_kernel`: 隠れ層から隠れ層への接続重みの初期化関数。デフォルトは `glorot_uniform`。
  * `bias`: ゼロで初期化されたバイアス項を含めるかどうか。デフォルトは `true`。

# フォワード

```
grucell(x, h)
grucell(x)
```

フォワードパスの引数は次のとおりです。

  * `x`: GRUへの入力。サイズ `in` のベクトルまたはサイズ `in x batch_size` の行列である必要があります。
  * `h`: GRUの隠れ状態。サイズ `out` のベクトルまたはサイズ `out x batch_size` の行列である必要があります。提供されない場合は、[`initialstates`](@ref) によって初期化されたゼロのベクトルであると見なされます。

タプル `(output, state)` を返します。ここで `output = h'` および `state = h'` です。新しい隠れ状態 `h'` はサイズ `out` または `out x batch_size` の配列です。

# 例

```jldoctest
julia> g = GRUCell(3 => 5)
GRUCell(3 => 5)     # 135 パラメータ

julia> h = zeros(Float32, 5); # 隠れ状態

julia> x = rand(Float32, 3, 4);  # in x batch_size

julia> y, h = g(x, h);
```
