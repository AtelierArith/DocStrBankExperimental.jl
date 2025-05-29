```
preamble
```

定数 [`TypstString`](@ref) は、[`render`](@ref) によって生成された Typst ソースファイルの先頭や、いくつかの `show` メソッドで使用されます。

[`set_preamble`](@ref) を使用して設定できます。

# 例

```jldoctest
julia> preamble
TypstString(TypstText("#set page(margin: 1em, height: auto, width: auto, fill: white)\n#set text(16pt, font: \"JuliaMono\")\n"))
```
