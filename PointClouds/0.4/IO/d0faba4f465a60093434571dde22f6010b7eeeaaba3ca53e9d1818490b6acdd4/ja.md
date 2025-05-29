```
getcrs([T], las::LAS)
```

[`LAS`](@ref)の座標参照系（CRS）を取得します。これは、`LAS`に含まれる形式のままか、型`T`に変換された形式で取得されます。LAS形式は、[GeoTIFF標準](https://docs.ogc.org/is/19-008r4/19-008r4.html)で定義されたバイナリ形式または、[OpenGIS®座標変換サービス標準](https://www.ogc.org/standards/ct/)で定義された一般的なテキスト（WKT）表現のいずれかでCRSデータを保存します。前者はカスタム`GeoKeys`型で表され、後者は`String`で表されます。現在、`GeoKeys`からWKT `String`への変換のみが実装されていますが、これにより`getcrs(String, las)`で取得したCRS情報を[Proj.jl](https://github.com/JuliaGeo/Proj.jl)などの他のライブラリに渡すことができます。ただし、変換は`GeoKeys`データの厳密な解釈を行うため、不完全または非標準のCRSデータを変換できない場合があります。
