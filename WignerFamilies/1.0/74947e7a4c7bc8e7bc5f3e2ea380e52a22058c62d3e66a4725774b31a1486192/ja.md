```
wigner3j_f(::Type{T}, j₂, j₃, m₂, m₃) where {T<:Real}
```

固定された j₂, j₃, m₂, m₃ に対して、すべての許可された j₁ を計算します。m₁=-m₂-m₃。

# 引数

  * `T::Type{<:Real}`: 出力配列の型
  * `j₂`: 量子数
  * `j₃`: 量子数
  * `m₂`: 量子数
  * `m₃`: 量子数

# 戻り値

  * `Tuple{Vector{Int}, Vector{T}}`: j₁ の値とウィグナー記号
