```
place(name::String)
place(name::String, type::Symbol)
```

PetriネットオブジェクトのためのPlace型のオブジェクトを作成します。注意: 許可されるプレースタイプは: :string, :control, :control_init, :counterです。

また、入力または出力プレースは:type :controlであってはなりません。

# 例

```julia-repl
julia> place("new_place", :string)
Place "new_place" created.

julia> place("in_place", :control)
Place "in_place" with control token created.
```

詳細は[`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref)を参照してください。
