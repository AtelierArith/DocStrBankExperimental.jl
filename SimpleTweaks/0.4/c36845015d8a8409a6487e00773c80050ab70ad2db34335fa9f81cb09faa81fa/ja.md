```
find_first_occurrence(array::AbstractArray{T}, val::T) where {T} -> Union(nothing,Int)
```

`array`内で`val`を検索し、最初の出現のインデックスを返します。

# 引数

  * `array::AbstractArray{T}`: 検索する配列、
  * `val::T`: 検索する値、

# キーワード

# 戻り値

  * `Int`: `array`内の`val`が位置するインデックス、または`array`内に`val`が見つからない場合は`nothing`。

# 例外
