```
    pdDocGetCosDoc(doc::PDDoc) -> CosDoc
```

PDFドキュメントフォーマットは2つのレイヤーで開発されています。論理的なPDFドキュメント情報は、COSと呼ばれる物理ファイル構造の上に表現されています。`CosDoc`はPDFドキュメントの物理ファイル構造へのアクセスオブジェクトです。直接APIが利用できない場合に、ドキュメント構造からPDF内部オブジェクトにアクセスするために使用されます。

COSレベルのAPIだけを使用してPDFのあらゆる側面にアクセスすることができます。ただし、PDF仕様を詳細に知っている必要があり、最も直感的ではありません。

# 例

```
julia> cosdoc = pdDocGetCosDoc(doc)

CosDoc ==>
	filepath:		/home/sambit/.julia/dev/PDFIO/test/PDFTest-0.0.4/stillhq/3.pdf
	size:			817945
	hasNativeXRefStm:	 false
	Trailer dictionaries: 
	<<
	/ID	[<2ff783c9846ab546bd49f709cb7be307> <2ff783c9846ab546bd49f709cb7be307> ]
	/Size	163
	/Prev	814755
	/Info	146 0 R
	/Root	154 0 R
>>
	<<
	/ID	[<2ff783c9846ab546bd49f709cb7be307> <2ff783c9846ab546bd49f709cb7be307> ]
	/Size	153
>>
```
