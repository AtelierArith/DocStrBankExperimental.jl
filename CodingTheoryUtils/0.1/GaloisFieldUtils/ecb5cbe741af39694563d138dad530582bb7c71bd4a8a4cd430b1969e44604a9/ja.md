```
hex(v::Vector{F2})::String
```

F2上のバイナリベクトルを16進数の文字列表現に変換します。

# 引数

  * `v::Vector{F2}`: F2上のバイナリベクトル

# 戻り値

  * `String`: 入力ベクトルの16進数の文字列表現

# 例

```julia
julia> v = [F2(1), F2(0), F2(1), F2(0)]
julia> hex(v)
"a"  # 1010を16進数で表現

julia> v = [F2(1), F2(1), F2(1), F2(1), F2(0), F2(0), F2(0), F2(0)]
julia> hex(v)
"f0"  # 11110000を16進数で表現
```
