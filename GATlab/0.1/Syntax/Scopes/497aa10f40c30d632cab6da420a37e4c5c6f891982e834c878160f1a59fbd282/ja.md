`retag(replacements::Dict{ScopeTag, ScopeTag}, x::T) where {T} -> T`

`x`の構造を再帰的にたどり、ScopeTag `t`の任意のインスタンスを`get(replacements, t, t)`で置き換えます。この関数を、内部にScopeTagsを持つ構造体に対してオーバーロードします。
