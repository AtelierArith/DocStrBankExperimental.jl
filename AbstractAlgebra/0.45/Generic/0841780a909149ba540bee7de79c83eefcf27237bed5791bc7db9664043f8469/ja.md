```
setpermstyle(format::Symbol)
```

置換が表示されるスタイルを選択します（REPL内または一般的に文字列として）。これは次のいずれかです。

  * `:array` - 整数のベクトルとして、$n$番目の位置が$n$の値を表します。
  * `:cycles` - 数学者にとってより馴染みのある、互いに素なサイクルへの分解として、$n$の値はサイクル内の$n$の直後にあるエントリによって表されます（デフォルト）。

違いは純粋に美的なものです。

# 例

```jldoctest
julia> setpermstyle(:array)
:array

julia> Perm([2,3,1,5,4])
[2, 3, 1, 5, 4]

julia> setpermstyle(:cycles)
:cycles

julia> Perm([2,3,1,5,4])
(1,2,3)(4,5)
```
