```
@typst_str("s")
typst"s"
```

[`TypstString`](@ref)を構築します。

制御文字はエスケープされますが、二重引用符とバックスラッシュは`@raw_str`と同様に扱われます。値は`TypstString`コンストラクタを呼び出すことで補間できますが、型名の代わりにバックスラッシュを使用します。補間構文は引用符と同様にエスケープできます。

!!! tip
    [`show(::IO, ::MIME"text/typst", ::Typst)`](@ref)を使用して、`IO`に直接印刷します。

    また、[I/Oのための文字列補間を避ける](https://docs.julialang.org/en/v1/manual/performance-tips/#Avoid-string-interpolation-for-I/O)というパフォーマンスタイプも参照してください。


# 例

```jldoctest
julia> x = 1;

julia> typst"$ \(x; mode = math) / \(x + 1; mode = math) $"
typst"$ 1 / 2 $"

julia> typst"\(x//2)"
typst"$1 / 2$"

julia> typst"\(x // 2; mode = math)"
typst"(1 / 2)"

julia> typst"\\(x)"
typst"\\(x)"
```
