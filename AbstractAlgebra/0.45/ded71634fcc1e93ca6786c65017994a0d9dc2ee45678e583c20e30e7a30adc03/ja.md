```
inflate(f::T, vars::Vector{T}, shift::Vector{Int}, defl::Vector{Int}) where T <: MPolyRingElem
```

与えられた変数の指数が指定されたデフレーション指数（インフレーション係数の配列として供給）によって膨張（乗算）され、その後、指定されたシフト（再びシフトの配列として供給）によって増加した同じ係数を持つ多項式を返します。
