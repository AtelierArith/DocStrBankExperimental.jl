```
interval_isapprox(a::Interval, b::Interval; kwargs)
```

区間 $a$ と $b$ が近似的に等しいかどうかをチェックします。つまり、両方の下限と上限が近似的に等しいことを意味します。

### キーワード

`Base.isapprox` と同じ

### 例

```jldoctest
julia> a = 1..2
[1, 2]

julia> b = a + 1e-10
[1, 2.00001]

julia> interval_isapprox(a, b)
true

julia> interval_isapprox(a, b; atol=1e-15)
false
```
