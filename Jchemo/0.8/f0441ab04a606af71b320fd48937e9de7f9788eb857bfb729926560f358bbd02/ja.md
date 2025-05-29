```
recod_miss(X; miss = nothing)
recod_miss(df; miss = nothing)
```

データセット内のデータを欠損として宣言します。

  * `X` : データセット（配列）。
  * `miss` : データセット内で欠損として宣言されるデータを識別するために使用されるコード（`Missing`型）。

データフレームに特有のもの：

  * `df` : データセット（データフレーム）。

`miss = nothing`の場合、`X`または`df`内で`missing`を許可するだけの動作があります。

例を参照してください。

## 例

```julia
using Jchemo, DataFrames

X = hcat(1:5, [0, 0, 7., 10, 1.2])
X_miss = recod_miss(X; miss = 0)

df = DataFrame(i = 1:5, x = [0, 0, 7., 10, 1.2])
df_miss = recod_miss(df; miss = 0)

df = DataFrame(i = 1:5, x = ["0", "0", "c", "d", "e"])
df_miss = recod_miss(df; miss = "0")
```
