```
reorder_dimension_by_tunables!(dest::AbstractArray, sys::AbstractSystem, arr::AbstractArray, syms; dim = 1)
```

次元 `dim` の `arr` の値の順序がシステムの調整可能なパラメータの順序に対応していると仮定すると、`syms` で説明された順序に従ってそれらを再配置します。`syms` は `tunable_parameters(sys)` の順列でなければなりません。結果は `dest` に書き込まれます。`dest``と`arr`の`size`は等しくなければなりません。`dest` を返します。

参照: [`MTKParameters`](@ref), [`tunable_parameters`](@ref), [`reorder_dimension_by_tunables`](@ref).
