```
@sco(f::Function, types;
    process::Union{Nothing,Function}=nothing, post::Function=identity)
```

`f()`のコードと出力を表示します。コードのみを表示するには、[`@sc`](@ref)を使用してください。`process`と`post`に関する詳細は[`sco`](@ref)を参照してください。
