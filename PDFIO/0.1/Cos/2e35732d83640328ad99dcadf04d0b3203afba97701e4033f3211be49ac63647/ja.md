```
    cosDocOpen(filepath::AbstractString) -> CosDoc
```

PDFドキュメントの物理ファイルとファイル構造へのアクセスを提供します。`CosDoc`を返し、その後PDFファイルへのすべてのクエリに使用できます。オブジェクトの使用が終わったら、`cosDocClose`でドキュメントを解放することを忘れないでください。
