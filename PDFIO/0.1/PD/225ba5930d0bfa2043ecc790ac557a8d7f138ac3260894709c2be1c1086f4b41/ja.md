```
    pdDocGetNamesDict(doc::PDDoc) -> CosObject
```

PDF内の一部の情報は、必ずしも辞書ではない名前と値のペアとして保存されています。それらはすべて集約され、文書カタログ内の1つの`names`辞書オブジェクトからアクセスできます。このメソッドは、PDFファイル内のそのような値へのアクセスを提供します。すべてのPDF文書に名前辞書があるわけではありません。そのような場合、`CosNull`オブジェクトが返されることがあります。

詳細については、PDF仕様を参照してください。

# 例

```
julia> pdDocGetNamesDict(doc)

220 0 obj
<<
	/IDS	123 0 R
	/Dests	119 0 R
	/URLS	124 0 R
>>
endobj
```
