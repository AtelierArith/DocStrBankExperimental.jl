```
deflate(f::MPolyRingElem, vars::Vector{Int}, shift::Vector{Int}, defl::Vector{Int})
```

与えられたシフト（シフトの配列として供給される）によっていくつかの変数（変数インデックスの配列として供給される）の指数が減少したが、$f$と同じ係数を持つ多項式を返します。その後、与えられた指数（再び除去因子の配列として供給される）によって除去（除算）されます。アルゴリズムは、自動的に除去が$0$の場合は$1$に置き換え、$0$による除算を避けます。
