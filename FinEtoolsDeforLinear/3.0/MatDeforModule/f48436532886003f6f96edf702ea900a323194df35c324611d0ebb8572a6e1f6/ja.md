```
tens4deviator!(t::Array{T, 4}) where {T}
```

4次の偏差テンソルを計算します。

この4次テンソルとの二重収束は、2次テンソルの偏差部分を生成します。

# 例

偏差テンソルと2次テンソル `S` の積は 

```
t = fill(0.0, 3, 3, 3, 3)
tens4deviator!(t)
S = rand(3, 3)
tS = fill(0.0, 3, 3)
tens4dot2!(tS, t, S)
@show tr((S - tr(S)/3*I) ), tr(tS)
```
