```
tens4tracor!(t::Array{T, 4}) where {T}
```

4次のトレーステンソルを計算します。

この4次テンソルとの二次テンソルの二重収束は、二次テンソルの球面部分を生成します。

# 例

トレーステンソルと二次テンソル `S` の積は 

```
t = fill(0.0, 3, 3, 3, 3)
tens4tracor!(t)
S = rand(3, 3)
tS = fill(0.0, 3, 3)
tens4dot2!(tS, t, S)
@show tr(S) * I - tS
```
