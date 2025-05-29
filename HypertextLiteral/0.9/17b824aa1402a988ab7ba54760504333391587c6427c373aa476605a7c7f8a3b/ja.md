```
HypertextLiteral
```

`HypertextLiteral`モジュールは、ハイパーテキストエスケープコンテキストを意識した補間を実装する`@htl`マクロをエクスポートします。また、`<script>`タグ内のJavaScriptのエスケープも提供します。

```jldoctest
julia> v = "<1 Brown \"M&M's\"!";

julia> @htl "<span>$v</span>"
<span>&lt;1 Brown &quot;M&amp;M&apos;s&quot;!</span>

julia> @htl "<script>console.log($v)</script>"
<script>console.log("<1 Brown \"M&M's\"!")</script>
```

Juliaの値をJavaScriptの値にエスケープするのは、デフォルトではエクスポートされていない`js`関数を使用して行われます。

```jldoctest
julia> v = "<1 Brown \"M&M's\"!";

julia> @htl "<div onclick='alert($(HypertextLiteral.js(v)))'>"
<div onclick='alert(&quot;&lt;1 Brown \&quot;M&amp;M&apos;s\&quot;!&quot;)'>
```

エクスポートされていない非標準の文字列リテラル`@htl_str`もあります。これは動的に構築されたテンプレートで使用できます。

参照: [`@htl`](@ref), [`HypertextLiteral.@htl_str`](@ref)
