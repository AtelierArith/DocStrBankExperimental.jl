```
de2f2(d::Integer; width::Int = 0)::Vector{F2}
```

10進数をF2要素のベクターに変換します。

# 引数

  * `d::Integer`: 変換する10進数
  * `width::Int = 0`: 出力ベクターの希望する幅。0の場合、必要な最小幅が使用されます。

# 戻り値

  * `Vector{F2}`: 入力数の2進数形式を表すF2要素のベクター

# 例

```julia
julia> de2f2(5)
3-element Vector{F2}:
 1
 0
 1

julia> de2f2(5, width=4)
4-element Vector{F2}:
 1
 0
 1
 0
```
