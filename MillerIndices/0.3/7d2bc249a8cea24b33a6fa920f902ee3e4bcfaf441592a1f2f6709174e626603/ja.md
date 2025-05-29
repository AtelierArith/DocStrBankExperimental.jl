```
m_str(s)
```

ミラー指数またはミラー–ブラバイス指数を迅速に生成します。

# 例

```jldoctest
julia> m"[-1, 0, 1]"
3-element Miller:
 -1
  0
  1

julia> m"<2, -1, -1, 3>"
4-element MillerBravais:
  2
 -1
 -1
  3

julia> m"(-1, 0, 1)"
3-element ReciprocalMiller:
 -1
  0
  1

julia> m"(1, 0, -1, 0)"
4-element ReciprocalMillerBravais:
  1
  0
 -1
  0
```
