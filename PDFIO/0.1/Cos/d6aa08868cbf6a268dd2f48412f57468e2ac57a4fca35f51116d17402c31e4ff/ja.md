```
    CosObject
```

PDFは、辞書、配列、木などの内部データ構造を持つ構造化された文書形式です。`CosObject`は、これらのオブジェクトにアクセスし、詳細な情報を取得するためのインターフェースです。COSレイヤーで定義されているにもかかわらず、これらのタイプのオブジェクトはほぼすべてのAPIから返されます。したがって、`Cos`レイヤーを使用する必要があるかどうかにかかわらず、オブジェクトには別の重要性があります。以下はオブジェクトの階層です。

```
CosObject                           Abstract
    CosNull                         Value (CosNullType)
CosString                           Abstract
CosName                             Concrete
CosNumeric                          Abstract
    CosInt                          Concrete
    CosFloat                        Concrete
CosBoolean                          Concrete
    CosTrue                         Value (CosBoolean)
    CosFalse                        Value (CosBoolean)
CosDict                             Concrete
CosArray                            Concrete
CosStream                           Concrete (always wrapped as an indirect object)
CosIndirectObjectRef                Concrete (only useful when CosDoc is available)
```

*注*: 読者APIとして、`CosObject`タイプのいずれかをインスタンス化する必要はないかもしれません。これらは通常、PDFファイルの解析の結果として生成されます。
