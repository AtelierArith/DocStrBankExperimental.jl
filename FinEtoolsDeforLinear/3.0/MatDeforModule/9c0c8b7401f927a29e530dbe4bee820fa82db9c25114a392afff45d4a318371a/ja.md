```
tens4transposor!(t::Array{T, 4}) where {T}
```

4次の転置テンソルを計算します。

# 例

転置テンソルと2次のテンソル `S` の積は 

```
t = fill(0.0, 3, 3, 3, 3)
tens4transposor!(t)
S = rand(3, 3)
tS = fill(0.0, 3, 3)
tens4dot2!(tS, t, S)
@show S' - tS
```
