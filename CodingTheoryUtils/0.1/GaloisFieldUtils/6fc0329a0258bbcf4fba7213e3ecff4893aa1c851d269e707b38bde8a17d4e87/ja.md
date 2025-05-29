```
de2bi(d::Integer; width::Int = 0)::Vector{Int}
```

10進数を2進数ベクトルに変換します。

# 引数

  * `d::Integer`: 変換する10進数
  * `width::Int = 0`: 出力ベクトルの希望の幅。0の場合、必要な最小幅が使用されます。

# 戻り値

  * `Vector{Int}`: 入力数の2進数形式を表す0と1のベクトル

# 例

```julia
julia> de2bi(5)
3-element Vector{Int64}:
 1
 0
 1

julia> de2bi(5, width=4)
4-element Vector{Int64}:
 1
 0
 1
 0
```
