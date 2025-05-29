```
@returnmissing(expr)
```

`expr` が `missing` に評価される場合、`missing` を返します。    

# 例

```jldoctest; output=false
finner(x::Real) = x*2
f1(x) = finner(x)
f2(x) = finner(@returnmissing(x))
f1(3) == f2(3) == 2*3
# エラー: f1(missing)
ismissing(f2(missing))
# 出力
true
```
