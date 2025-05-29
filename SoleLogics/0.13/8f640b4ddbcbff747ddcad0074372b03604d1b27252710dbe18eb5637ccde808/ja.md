```
struct Atom{V} <: AbstractAtom
    value::V
end
```

最も単純なアトムの実装で、`value`をラップしています。

[`AbstractAtom`](@ref)、[`value`](@ref)、[`check`](@ref)、[`SyntaxToken`](@ref)も参照してください。
