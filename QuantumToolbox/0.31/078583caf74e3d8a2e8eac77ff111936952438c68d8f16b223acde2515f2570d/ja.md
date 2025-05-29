```
eigenstates(A::QuantumObject; sparse::Bool=false, kwargs...)
```

固有値と対応する固有ベクトルを計算します

# 引数

  * `A::QuantumObject`: 固有値と固有ベクトルを解くための[`QuantumObject`](@ref)
  * `sparse::Bool`: `false`の場合は[`eigen(A::QuantumObject; kwargs...)`](@ref)を呼び出し、そうでなければ[`eigsolve`](@ref)を呼び出します。デフォルトは`false`です。
  * `kwargs`: ソルバーに渡される追加のキーワード引数。`sparse=true`の場合、キーワード引数は[`eigsolve`](@ref)に渡され、それ以外の場合は[`eigen`](@ref)に渡されます。

# 戻り値

  * `::EigsolveResult`: 固有値、固有ベクトル、およびソルバーからのいくつかの情報を含みます。詳細は[`EigsolveResult`](@ref)を参照してください。
