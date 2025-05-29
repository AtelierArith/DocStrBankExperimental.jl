```
    pdDocOpen(filepath::AbstractString) -> PDDoc
```

PDFドキュメントを開き、PDFファイルへの後続のクエリのためのPDDocドキュメントオブジェクトを提供します。`filepath`は、相対パスまたは絶対パス形式のPDFファイルへのパスです。

オブジェクトがもはや必要でなくなったら、`pdDocClose`でドキュメントを解放することを忘れないでください。`doc`には特定のメンバーがありますが、通常は不透明なハンドルとして考慮されるべきです。

# 例

```
julia> doc = pdDocOpen("test/PDFTest-0.0.4/stillhq/3.pdf")

PDDoc ==>

CosDoc ==>
	filepath:		/home/sambit/.julia/dev/PDFIO/test/PDFTest-0.0.4/stillhq/3.pdf
	size:			817945
	hasNativeXRefStm:	 false
	Trailer dictionaries: 
	<<
	/Info	146 0 R
	/Prev	814755
	/Size	163
	/Root	154 0 R
	/ID	[<2ff783c9846ab546bd49f709cb7be307> <2ff783c9846ab546bd49f709cb7be307> ]
>>
	<<
	/Size	153
	/ID	[<2ff783c9846ab546bd49f709cb7be307> <2ff783c9846ab546bd49f709cb7be307> ]
>>

Catalog:
154 0 obj
<<
	/Type	/Catalog
	/Pages	152 0 R
>>
endobj

isTagged: none
```
