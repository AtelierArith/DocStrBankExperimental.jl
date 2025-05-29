```
parse_header(
    index::Index,
    header::AbstractString,
    args::Vector{String}=[],
    flags=CXTranslationUnit_None,
) -> TranslationUnit
```

与えられたヘッダーのためのTranslationUnitを返します。これはパースのための主なエントリーポイントです。

# 引数

  * `header::AbstractString`: パースするヘッダーファイル。
  * `index::Index`: CXIndexポインタ（再割り当てを避けるために渡します）。
  * `args::Vector{String}`: 文字列配列としてのコンパイラスイッチ、例: ["-x", "c++", "-fno-elide-type"]。
  * `flags`: CXTranslationUnit_Flagsのビット単位のOR。

[`parse_headers`](@ref)も参照してください。
