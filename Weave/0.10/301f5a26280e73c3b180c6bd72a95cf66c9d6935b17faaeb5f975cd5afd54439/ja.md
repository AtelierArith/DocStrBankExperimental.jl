```
include_weave(source::AbstractString, informat::Union{Nothing,AbstractString} = nothing)
include_weave(m::Module, source::AbstractString, informat::Union{Nothing,AbstractString} = nothing)
```

Weaveドキュメントからのコードを含め、ドキュメント内のすべてのコードに対して`include_string`を呼び出します。コードは、インクルードドキュメントのパスで実行されます。
