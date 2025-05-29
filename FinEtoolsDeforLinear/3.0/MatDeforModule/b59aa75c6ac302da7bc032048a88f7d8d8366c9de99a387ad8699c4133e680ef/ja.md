```
tens4symmetrizor!(t::Array{T, 4}) where {T}
```

4次の対称化テンソルを計算します。

この4次テンソルとの二次テンソルの二重収束は、二次テンソルの対称部分を生成します。

# 例

対称化テンソルと二次テンソル `S` の積は 

```
t = fill(0.0, 3, 3, 3, 3)
tens4symmetrizor!(t)
S = rand(3, 3)
tS = fill(0.0, 3, 3)
tens4dot2!(tS, t, S)
@show (S + S')/2 * I - tS
```
