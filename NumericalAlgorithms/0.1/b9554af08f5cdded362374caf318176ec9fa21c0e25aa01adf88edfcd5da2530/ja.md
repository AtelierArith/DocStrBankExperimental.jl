```
CalcDoubleIntegral(f::Function, a::Real, b::Real, c::Real, d::Real, n::UInt64)
```

関数 f(x,y) の二重積分を領域 D=[a, b] x [c(a), d(b)] で計算します（ダブルシンプソン法）。

```
b                        
.- d(x)                  
|    .-                  
|    |                   
|   -'  f(x, y) . dy . dx
-'  c(x)                  
a
```
