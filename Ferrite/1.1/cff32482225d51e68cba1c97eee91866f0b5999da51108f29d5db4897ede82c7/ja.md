```
add_sparsity_entries!(
    sp::AbstractSparsityPattern,
    dh::DofHandler,
    ch::Union{ConstraintHandler, Nothing} = nothing;
    topology = nothing,
    keep_constrained::Bool = true,
    coupling = nothing,
    interface_coupling = nothing,
)
```

一般的なタスクである[`add_cell_entries!`](@ref)、[`add_interface_entries!`](@ref)、および[`add_constraint_entries!`](@ref)を呼び出すための便利なメソッドであり、渡される引数に応じて動作します：

  * `add_cell_entries!`は常に呼び出されます
  * `topology`が提供されている場合（すなわち`nothing`でない場合）、`add_interface_entries!`が呼び出されます
  * ConstraintHandlerが提供されている場合、`add_constraint_entries!`が呼び出されます

引数およびキーワード引数の詳細については、それぞれの関数を参照してください。
