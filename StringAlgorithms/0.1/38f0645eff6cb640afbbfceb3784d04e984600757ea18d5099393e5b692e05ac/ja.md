```julia
prefix_function(v)

```

与えられたベクトルの各接頭辞について、その非自明な接頭辞（それ自身ではない）が接尾辞と等しい最大の長さを計算します。

例えば、文字列 `ababc` の場合、

  * `p[1] = 0`
  * `p[2] = 0`
  * `p[3] = 1`、接頭辞 `aba` は接頭辞 `a` と接尾辞 `a` の両方を持つため
  * `p[4] = 2`、接頭辞 `abab` は接頭辞 `ab` と接尾辞 `ab` の両方を持つため
  * `p[5] = 0`

# サンプル使用法

  * すべての一致を見つける（KMPアルゴリズム）

```jldoctest
# 次の関数は、与えられたベクトル内のパターンのすべての出現を見つけ、重複するものも含みます。
function findall(pattern, s)
    n, m = length(s), length(pattern)
    tmp = vcat(collect(pattern), [nothing], collect(s))
    p = prefix_function(tmp)
    return [i-m+1:i for i in 1:n if p[i+m+1] == m]
end

findall("aba", "ddabababacc")

# 出力

3-element Vector{UnitRange{Int64}}:
 3:5
 5:7
 7:9
```
