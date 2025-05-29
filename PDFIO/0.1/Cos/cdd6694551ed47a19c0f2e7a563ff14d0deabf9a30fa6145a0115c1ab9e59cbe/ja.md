```
    cosDocGetObject(doc::CosDoc, obj::CosObject) -> CosObject
```

PDFオブジェクトはファイル内に分散しており、ある場所から別の場所へ相互参照することができます。これを間接オブジェクト参照と呼びます。しかし、実際の情報を抽出するには、完全なオブジェクト（直接オブジェクト）へのアクセスが必要です。このメソッドは、ドキュメント構造内でオブジェクトを検索した後に直接オブジェクトへのアクセスを提供します。間接オブジェクト参照が`obj`パラメータとして渡されると、完全な`間接オブジェクト`（参照とオブジェクトのすべての内容）が返されます。メソッドに渡された`直接オブジェクト`は、翻訳されることなくそのまま返されます。これにより、ユーザーは内容にアクセスする前にオブジェクトのタイプを確認する必要がなくなります。

# 例

```
julia> cosDocGetObject(doc.cosDoc, CosIndirectObjectRef(555, 0))

555 0 obj
<<
	/Count	18
	/Last	629 0 R
	/First	556 0 R
>>
endobj

julia> cosDocGetObject(doc.cosDoc, cn"DirectObject")
/DirectObject
```
