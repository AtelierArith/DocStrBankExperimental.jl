```
AnnotatedChar{S <: AbstractChar} <: AbstractChar
```

注釈付き文字。

より具体的には、これは他の[`AbstractChar`](@ref)の周りのシンプルなラッパーであり、ラップされた文字とともに任意のラベル付き注釈のリスト（`@NamedTuple{label::Symbol, value}`）を保持します。

関連情報: [`AnnotatedString`](@ref), [`annotatedstring`](@ref), `annotations`, および `annotate!`。

# コンストラクタ

```julia
AnnotatedChar(s::S) -> AnnotatedChar{S}
AnnotatedChar(s::S, annotations::Vector{@NamedTuple{label::Symbol, value}})
```

# 例

```julia-repl
julia> AnnotatedChar('j', :label => 1)
'j': ASCII/Unicode U+006A (category Ll: Letter, lowercase)
```
