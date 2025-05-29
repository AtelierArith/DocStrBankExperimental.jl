```
    pdPageGetContents(page::PDPage) -> CosObject
```

ページレンダリングオブジェクトは通常、PDFファイル内の`CosStream`オブジェクトに格納されます。このメソッドはストリームオブジェクトへのアクセスを提供します。

詳細についてはPDF仕様を参照してください。

# 例

```
julia> pdPageGetContents(page)

448 0 obj
<<
	/Length	437
	/FFilter	/FlateDecode
	/F	(/tmp/tmpZnGGFn/tmp5J60vr)
>>
stream
...
endstream
endobj
```
