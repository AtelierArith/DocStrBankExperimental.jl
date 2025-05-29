```
CalcSingleIntegral(f::Function, a::Real, b::Real, n::UInt64)
```

f 関数の a から b までの積分を計算します（合成シンプソン法）。

```
b          
⌠          
⌡ f(x) ⋅ dx
a
```
