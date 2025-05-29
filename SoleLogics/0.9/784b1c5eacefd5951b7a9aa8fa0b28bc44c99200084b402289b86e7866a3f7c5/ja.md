```
abstract type SyntaxLeaf <: AbstractSyntaxStructure end
```

原子的論理要素、例えば `Truth` 値や `Atom` のようなものです。`SyntaxLeaf` は `arity` がゼロであるため、木のような構文構造において子を持つことは許可されていません。

関連情報としては [`AbstractSyntaxStructure`](@ref)、[`arity`](@ref)、[`SyntaxBranch`](@ref) があります。
