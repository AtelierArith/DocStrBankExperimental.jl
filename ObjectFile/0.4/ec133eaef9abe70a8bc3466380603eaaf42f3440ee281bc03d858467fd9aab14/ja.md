```
シンボル
```

オブジェクトファイル内のシンボル（`SymtabEntry`）タイプのコレクションの概念に対する抽象化。`Symbols`オブジェクトはオブジェクトファイル内のシンボルのテーブルを含んでいると考えることができ、`SymtabEntry`/`SymbolRef`オブジェクトは実際のシンボルデータ自体を含んでいます。利用可能なAPI操作のリストは以下に示されており、サブクラスが実装しなければならないメソッドは強調表示されています。

### 作成

  * *Symbols()*

### 繰り返し

  * getindex()
  * *lastindex()*
  * length()
  * iterate()
  * eltype()

### 検索

  * findall()
  * findfirst()

### その他

  * *handle()*
