```julia
z_algorithm(v)

```

Zアルゴリズムは、与えられたベクトルの各接尾辞と全体のベクトル自体の最長共通接頭辞を計算します。特に、全体のベクトルのZ値は0に強制されます。

# サンプル使用法

> Zアルゴリズムの使用法は、接頭辞関数とほぼ同じです。


  * すべての一致を見つける

```jldoctest
# 次の関数は、与えられたベクトル内のパターンのすべての出現を見つけます（重複を含む）。
function findall(pattern, s)
    n, m = length(s), length(pattern)
    tmp = vcat(collect(pattern), [nothing], collect(s))
    z = z_algorithm(tmp)
    return [i:i+m-1 for i in 1:n if z[i+m+1] == m]
end

findall("aba", "ddabababacc")

# 出力

3-element Vector{UnitRange{Int64}}:
 3:5
 5:7
 7:9
```
