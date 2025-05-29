```
struct Atom{V} <: AbstractAtom
    value::V
end
```

最も単純なアトムの実装で、`value`をラップしています。

関連情報としては、[`AbstractAtom`](@ref)、[`value`](@ref)、[`check`](@ref)、[`SyntaxToken`](@ref)があります。
