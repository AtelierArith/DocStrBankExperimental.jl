```
abstract type AbstractRenderType end
```

レンダータイプのための一般的なトップレベルタイプです。ほとんどのデフォルトはここで設定されており、下位レベルで設定する必要がある理由がない限りそうなります。サブタイプは依然として抽象タイプであり、[`AbstractAscii`](@ref)、[`AbstractLatex`](@ref)、および[`AbstractHtml`](@ref)を含みます。
