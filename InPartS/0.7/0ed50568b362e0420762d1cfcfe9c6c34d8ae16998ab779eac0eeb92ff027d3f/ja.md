```
LineageRegistrar{T<:Integer} <: AbstractSeqRegistrar{T}
```

この[`AbstractSeqRegistrar`](@ref)の実装は、型`T`（デフォルトは`UInt64`）の連続番号を返すだけでなく、`parent`という辞書を使用して系譜を追跡することもできます。このレジストラで[`set_id!`](@ref)/[`get_id!`](@ref)を呼び出すと、自動的に辞書にエントリ`(newid -> parent_id)`として親が記録されます。
