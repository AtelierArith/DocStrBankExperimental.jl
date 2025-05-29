```
RBF(a::T, b::T, sigma::T) where T <: Number
RBF(a::T, b::T, sigma::T) where T <: AbstractArray
RBF(params::Dict{String, T})
RBF(params::DataFrame)
RBF(params::YAXArray)
```

放射基底関数 (RBF) カーネル `exp((-1.0 * (a - b) ^ 2.0) / (2.0 * sigma ^ 2.0))` を計算します。この関数は、数値、配列、辞書、データフレーム、および YAXArray など、さまざまな入力タイプをサポートしています。

# 引数

  * `a`: RBF カーネルの最初のパラメータ。数値または配列であることができます。
  * `b`: RBF カーネルの2番目のパラメータ。数値または配列であることができます。
  * `sigma`: RBF カーネルの長さスケールパラメータ。数値または配列であることができます。
  * `params`: "a"、"b"、および "sigma" のパラメータを含む辞書、データフレーム、または YAXArray。

# 戻り値

  * RBF カーネルの結果。出力タイプは入力タイプに依存します：

      * `a`、`b`、および `sigma` が数値の場合、結果は数値です。
      * `a`、`b`、および `sigma` が配列の場合、結果は要素ごとに操作が適用された配列です。
      * `params` が使用される場合、結果は `params` の形式に一致します（辞書、DataFrame、または YAXArray のいずれか）。

# 例

```julia
# 数値を使用
result = RBF(1, 2, 0.5)

# 配列を使用
result = RBF([1, 2, 3], [4, 5, 6], [0.5, 0.5, 0.5])

# 辞書を使用
result = RBF(Dict("a" => 1, "b" => 2, "sigma" => 0.5))

# データフレームを使用
df = DataFrame(; a=[1, 2, 3], b=[4, 5, 6], sigma=[0.5, 0.5, 0.5])
result = RBF(df)
```
