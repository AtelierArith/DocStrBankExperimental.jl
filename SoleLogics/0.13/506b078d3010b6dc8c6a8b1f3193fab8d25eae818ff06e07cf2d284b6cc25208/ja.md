```
abstract type SyntaxLeaf <: SyntaxStructure end
```

真理値や原子のような原子的な論理要素。`SyntaxLeaf`は`arity`がゼロであるため、木のような構文構造において子を持つことは許可されていません。

# インターフェース

  * `syntaxstring(s::SyntaxLeaf; kwargs...)::String`
  * `dual(s::SyntaxLeaf)::SyntaxLeaf`
  * `hasdual(s::SyntaxLeaf)::Bool`

参照: [`SyntaxStructure`](@ref),  [`arity`](@ref), [`SyntaxBranch`](@ref).
