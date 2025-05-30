```
IPv6(host::Integer) -> IPv6
```

整数としてフォーマットされたIPアドレス`host`からIPv6オブジェクトを返します。

# 例

```jldoctest
julia> IPv6(3223256218)
ip"::c01e:fc9a"
```
