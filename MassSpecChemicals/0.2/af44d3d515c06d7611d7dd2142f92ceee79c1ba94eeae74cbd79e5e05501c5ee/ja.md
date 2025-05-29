```
real_interval(val, lop = <=, rop = <=)
real_interval(ct::Criteria, lop = <=, rop = <=)
real_interval(val::Missing, lop = <=, rop = <=) = missing
real_interval(val::RealIntervals, lop = <=, rop = <=) = val
```

`RealInterval`を構築します。

`missing`、基準、実数区間以外の値が与えられた場合、`-abs(val)`から`abs(val)`までの実数区間を構築します。

基準が与えられた場合、その基準値が実数区間になる基準を構築します。

# 例

```julia
julia> ct = Criteria(10, 0.2);

julia> peak_crit = real_interval(ct);

julia> qualified_peak(x, x̂, ct) = all(c -> in(x - x̂, c), ct(x̂)); # xとx̂の差は±10および±20%の範囲内である必要があります

julia> peak_crit(100) # 真の値100で基準を作成
([-10, 10], [-20, 20])

julia> peak_crit(10) # 真の値10で基準を作成
([-10, 10], [-2, 2])

julia> qualified_peak(85, 100, peak_crit)
false

julia> qualified_peak(9, 10, peak_crit)
true 

```
