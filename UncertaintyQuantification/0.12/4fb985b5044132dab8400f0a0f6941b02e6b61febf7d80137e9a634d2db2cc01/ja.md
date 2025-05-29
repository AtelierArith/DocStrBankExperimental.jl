```
ResponseSurface(data::DataFrame, dependendVarName::Symbol, deg::Int, dim::Int)
```

与えられた次数の多項式最小二乗回帰を使用して応答面を作成します。

# 例

```jldoctest; filter = r"(\d*)\.(\d{12})\d+" => s"\1.\2***"
julia> data = DataFrame(x = 1:10, y = [1, 4, 10, 15, 24, 37, 50, 62, 80, 101]);

julia> rs = ResponseSurface(data, :y, 2)
ResponseSurface([0.48333333333332457, -0.23863636363636026, 1.0189393939393936], :y, [:x], 2, Monomials.Monomial[1, x1, x1²])
```
