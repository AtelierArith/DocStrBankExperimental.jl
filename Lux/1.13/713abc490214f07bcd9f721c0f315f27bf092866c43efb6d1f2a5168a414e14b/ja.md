```
Bilinear((in1_dims, in2_dims) => out, activation=identity; init_weight=nothing,
         init_bias=nothing, use_bias=True())
Bilinear(in12_dims => out, activation=identity; init_weight=nothing,
         init_bias=nothing, use_bias=True())
```

2つの入力と出力の間に全結合層を作成し、[`Dense`](@ref)とその他は類似しています。ベクトル `x` と `y` が与えられた場合、その出力は別のベクトル `z` であり、すべての `i in 1:out` に対して次のようになります：

`z[i] = activation(x' * W[i, :, :] * y + bias[i])`

もし `x` と `y` が行列であれば、出力 `z = B(x, y)` の各列はこの形式になります。ここで、`B` はBilinear層です。

## 引数

  * `in1_dims`: `x` の入力次元数
  * `in2_dims`: `y` の入力次元数
  * `in12_dims`: 指定されている場合、`in1_dims = in2_dims = in12_dims`
  * `out`: 出力次元数
  * `activation`: 活性化関数

## キーワード引数

  * `init_weight`: 重み行列の初期化子（`weight = init_weight(rng, out_dims, in1_dims, in2_dims)`）。`nothing` の場合、`-bound` と `bound` の範囲で一様分布を使用します。ここで `bound = inv(sqrt(in1_dims))` です。
  * `init_bias`: バイアスベクトルの初期化子（`use_bias=false` の場合は無視されます）。`nothing` の場合、`-bound` と `bound` の範囲で一様分布を使用します。ここで `bound = inv(sqrt(in1_dims))` です。
  * `use_bias`: この値を `false` に設定することで、学習可能なバイアスを完全に無効にできます。

## 入力

  * 次の内容を含む2タプル

      * `x` は `size(x, 1) == in1_dims` を満たす AbstractArray でなければなりません
      * `y` は `size(y, 1) == in2_dims` を満たす AbstractArray でなければなりません
  * 入力が AbstractArray の場合、`x = y` です。

## 戻り値

  * 次元 `(out_dims, size(x, 2))` の AbstractArray
  * 空の `NamedTuple()`

## パラメータ

  * `weight`: サイズ `(out_dims, in1_dims, in2_dims)` の重み行列
  * `bias`: サイズ `(out_dims, 1)` のバイアス（`use_bias=true` の場合に存在）
