```
getdegree(N)
```

は、係数またはパドゥア点の数 `N` に基づいて総次数を計算します。`N` が可能なパドゥア点の数でない場合はエラーをスローします。公式は次の通りです。

$$
n = \frac{\sqrt{1 + 8N} - 3}{2}
$$

# 例

```jldoctest
julia> getdegree(105)
13

julia> getdegree(104)
ERROR: ArgumentError: number of Padua points or coeffs must be (n + 1) * (n + 2) ÷ 2
[...]
```
