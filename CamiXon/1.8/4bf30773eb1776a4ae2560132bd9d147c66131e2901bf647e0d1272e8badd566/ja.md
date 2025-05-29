```
svp(atomicnumber::Int, temp::Real)
svp(element::String, temp::Real)
```

与えられた温度 *T* (K) に対する特定の `element` の飽和蒸気圧 *p* (Pa) は、

$$
\mathrm{log_{e}}p=A+B/T+C\mathrm{log_{10}}T+D\cdot T/1000,
$$

ここで A,B,C,D は [`CamiXon.dictAntoineCoefficient`](@ref) に収集されたアンティワイン係数です。

#### 例:

```
julia> svp("Li", 623.0)
0.0015230367024569058
```
