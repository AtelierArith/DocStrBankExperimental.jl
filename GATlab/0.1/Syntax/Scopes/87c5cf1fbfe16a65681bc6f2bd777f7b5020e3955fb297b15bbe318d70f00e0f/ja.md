`rename(tag::ScopeTag, replacements::Dict{Symbol, Symbol}, x::T) where {T} -> T`

`x`の構造を再帰的にたどり、スコープ`tag`内の任意の名前`n`を`get(replacements, n, n)`に変更します。この関数を名前を持つ構造体に対してオーバーロードします。
