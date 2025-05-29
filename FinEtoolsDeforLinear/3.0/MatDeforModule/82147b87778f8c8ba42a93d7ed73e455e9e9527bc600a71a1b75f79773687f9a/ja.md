```
tens4identity!(t::Array{T, 4}) where {T}
```

4次の単位テンソルを計算します。

# 例

単位テンソルと2次テンソル `S` の積は 

```
t = fill(0.0, 3, 3, 3, 3)
tens4identity!(t)
S = rand(3, 3)
tS = fill(0.0, 3, 3)
tens4dot2!(tS, t, S)
@show S - tS
```
