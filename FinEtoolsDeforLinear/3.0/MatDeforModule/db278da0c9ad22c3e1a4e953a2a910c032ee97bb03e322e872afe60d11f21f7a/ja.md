```
tens4skewor!(t::Array{T, 4}) where {T}
```

4次のスキュアテンソルを計算します。

この4次テンソルとの2次テンソルの二重収束は、2次テンソルのスキュー部分を生成します。

# 例

スキュアテンソルと2次テンソル `S` の積は 

```
t = fill(0.0, 3, 3, 3, 3)
tens4skewor!(t)
S = rand(3, 3)
tS = fill(0.0, 3, 3)
tens4dot2!(tS, t, S)
@show (S - S')/2 * I - tS
```
