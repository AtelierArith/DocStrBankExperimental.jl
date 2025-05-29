```
Dense(in_dims => out_dims, activation=identity; init_weight=nothing,
      init_bias=nothing, use_bias=True())
```

従来の完全接続層を作成します。フォワードパスは次のように与えられます: `y = activation.(weight * x .+ bias)`

## 引数

  * `in_dims`: 入力次元の数
  * `out_dims`: 出力次元の数
  * `activation`: 活性化関数

## キーワード引数

  * `init_weight`: 重み行列の初期化子（`weight = init_weight(rng, out_dims, in_dims)`）。`nothing`の場合、活性化関数に基づいて計算されたゲインを用いて[`kaiming_uniform`](@ref)を使用します（Pytorchの[`nn.init.calculate_gain`](https://pytorch.org/docs/stable/nn.init.html#torch.nn.init.calculate_gain)から取得）。
  * `init_bias`: バイアスベクトルの初期化子（`use_bias=false`の場合は無視されます）。`nothing`の場合、`-bound`と`bound`の範囲で一様分布を使用します。ここで、`bound = inv(sqrt(in_dims))`です。
  * `use_bias`: この値を`false`に設定することで、学習可能なバイアスを完全に無効にできます。

## 入力

  * `x`は`size(x, 1) == in_dims`である必要があるAbstractArrayです。

## 戻り値

  * 次元が`(out_dims, ...)`のAbstractArray。ここで`...`は`x`の次元です。
  * 空の`NamedTuple()`

## パラメータ

  * `weight`: サイズ`(out_dims, in_dims)`の重み行列
  * `bias`: サイズ`(out_dims, 1)`のバイアス（`use_bias=true`の場合に存在）
