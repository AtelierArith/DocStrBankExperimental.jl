```
findnan(y::AbstractVector; maxgap::Int=Inf)
```

ベクトル `y` の `NaN` 値のインデックスを見つけますが、`NaN` の連続が `maxgap` 以下である場合のみです。

# 引数

  * `y::AbstractVector`: `NaN` 値を検索するための入力ベクトル。
  * `maxgap::Int=Inf`: 結果に含めることができる連続した `NaN` 値の最大許容長。これを超える `NaN` の連続は無視されます。

# 戻り値

  * `Vector{Int}`: `NaN` 値が見つかったインデックスのベクトルで、`maxgap` 制約を考慮しています。

# 例

```julia
y = [1.0, NaN, NaN, 4.0, NaN, NaN, NaN, 8.0]
findnan(y, maxgap=2) # returns [2, 3]
findnan(y, maxgap=3) # returns [2, 3, 5, 6, 7]
```
