```
deflate(f::T, vars::Vector{T}, shift::Vector{Int}, defl::Vector{Int}) where T <: MPolyRingElem
```

与えられた変数の指数が指定されたシフト（シフトの配列として供給）によって減少し、その後、指定された指数（再び脱泡因子の配列として供給）によって脱泡（除算）された同じ係数を持つ多項式を返します。アルゴリズムは、自動的に脱泡が $0$ の場合は $1$ に置き換え、$0$ での除算を避けます。
