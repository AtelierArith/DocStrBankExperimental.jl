```
struct Statement{T}
    node::T
    type::Any
end
```

ユーザーによるローカル伝播やその他の分析形式を可能にするためのオプションの `type` フィールドを持つ `Core` ノードのラッパー。 [`Builder`](@ref) または [`Canvas`](@ref) の使用は、挿入または [`finish`](@ref) を呼び出す際にノードを自動的にラップまたはアンラップするため、ユーザーは型伝播に取り組んでいない限り、`Statement` インスタンスを直接見ることはありません。

`Core` ノードに関する詳細は、Julia の [lowered forms](https://docs.julialang.org/en/v1/devdocs/ast/#Lowered-form) に関するドキュメントを参照してください。
