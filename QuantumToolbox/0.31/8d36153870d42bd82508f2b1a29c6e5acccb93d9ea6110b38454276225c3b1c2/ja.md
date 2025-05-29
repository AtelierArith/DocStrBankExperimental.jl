```
eigenenergies(A::QuantumObject; sparse::Bool=false, kwargs...)
```

固有エネルギーを計算します

# 引数

  * `A::QuantumObject`: 固有値を解くための[`QuantumObject`](@ref)
  * `sparse::Bool`: `false`の場合は[`eigvals(A::QuantumObject; kwargs...)`](@ref)を呼び出し、それ以外の場合は[`eigsolve`](@ref)を呼び出します。デフォルトは`false`です。
  * `kwargs`: ソルバーに渡される追加のキーワード引数。`sparse=true`の場合、キーワード引数は[`eigsolve`](@ref)に渡され、それ以外の場合は[`eigen`](@ref)に渡されます。

# 戻り値

  * `::Vector{<:Number}`: 固有値のリスト
