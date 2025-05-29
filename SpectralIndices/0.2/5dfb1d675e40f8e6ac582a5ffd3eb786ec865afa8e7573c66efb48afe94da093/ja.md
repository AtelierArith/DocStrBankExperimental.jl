```
linear(a::Number, b::Number)
linear(a::AbstractArray, b::AbstractArray)
linear(params::Dict{String, T})
linear(params::DataFrame)
linear(params::YAXArray)
```

線形カーネル `a * b` を計算します。この関数は、数値、配列、辞書、データフレーム、および YAXArray など、さまざまな入力タイプをサポートしています。

# 引数

  * `a`: 線形カーネルの最初のパラメータ。数値または配列である可能性があります。
  * `b`: 線形カーネルの2番目のパラメータ。数値または配列である可能性があります。
  * `params`: パラメータ "a" と "b" を含む辞書、データフレーム、または YAXArray。

# 戻り値

  * `a * b` の結果。出力タイプは入力タイプに依存します：

      * `a` と `b` が数値の場合、結果は数値です。
      * `a` と `b` が配列の場合、結果は要素ごとの乗算を持つ配列です。
      * `params` が使用される場合、結果は `params` と同じ形式（辞書、DataFrame、または YAXArray）になります。

# 例

```julia
# 数値を使用
result = linear(2, 3)

# 配列を使用
result = linear([1, 2, 3], [4, 5, 6])

# 辞書を使用
result = linear(Dict("a" => 2, "b" => 3))

# データフレームを使用
df = DataFrame(; a=[1, 2, 3], b=[4, 5, 6])
result = linear(df)
```
