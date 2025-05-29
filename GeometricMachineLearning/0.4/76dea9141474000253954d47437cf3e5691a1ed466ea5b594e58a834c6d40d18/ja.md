```
split_and_flatten(input::AbstractArray)::AbstractArray
```

画像を*フラットなパッチ*に前処理します。

これは、入力データを変換器で簡単に処理できるように再配置します。

# 例

サイズが $6\times6$ の行列を考え、これをサイズ $3\times3$ のパッチに分割したいとします。

```jldoctest
using GeometricMachineLearning

input = [ 1  2  3  4  5  6; 
          7  8  9 10 11 12; 
         13 14 15 16 17 18;
         19 20 21 22 23 24; 
         25 26 27 28 29 30; 
         31 32 33 34 35 36]

split_and_flatten(input; patch_length = 3, number_of_patches = 4)

# 出力

9×4 Matrix{Int64}:
  1  19   4  22
  7  25  10  28
 13  31  16  34
  2  20   5  23
  8  26  11  29
 14  32  17  35
  3  21   6  24
  9  27  12  30
 15  33  18  36
```

ここでは、`split_and_flatten` が次のことを行うのがわかります：

1. 元の行列を4つの $3\times3$ 行列に*分割*し、次に
2. 各行列をサイズ $9$ の列ベクトルに*フラット化*します。

これらのベクトルは再びまとめられ、$9\times4$ の行列が得られます。

# 引数

オプションのキーワード引数は次のとおりです：

  * `patch_length`: デフォルトでは7です。
  * `number_of_patches`: デフォルトでは16です。

`split_and_flatten` の出力の最初と第二の軸のサイズは

1. $$
    \mathtt{path\_length}^2
    $$

    と
2. `number_of_patches` です。

```
