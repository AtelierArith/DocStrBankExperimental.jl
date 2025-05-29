```
sqrtmod(x::ZZRingElem, m::ZZRingElem)
```

$ m $ が素数である場合、$ x (\mod m) $ の平方根を返します。余りは $ [0, m) $ の範囲になります。$ m $ が素数でない場合、アルゴリズムが終了しない可能性があります。

# 例

```jldoctest
julia> sqrtmod(ZZ(12), ZZ(13))
5
```
