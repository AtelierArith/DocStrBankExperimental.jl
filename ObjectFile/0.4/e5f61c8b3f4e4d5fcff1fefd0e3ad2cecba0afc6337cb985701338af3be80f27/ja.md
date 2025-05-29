```
SymtabEntry
```

オブジェクトファイル内のシンボルの概念に対する抽象化です。このタイプは、組み込みのJulia `Symbol`タイプと衝突するため、`Symbol`名を使用しないので、代わりに`SymtabEntry`という名前が使用されます。ユーザーとしては、`SymbolRef`タイプがシンボルと対話するための主要な方法であるべきです。新しいオブジェクトファイル形式を追加する開発者としては、一部のメソッドは`SymtabEntry`をサポートし、他のメソッドは`SymbolRef`のみをサポートする必要があります。`SymtabEntry`で動作する任意のメソッドは、`SymbolRef`でも動作する必要があることに注意してください。`SymbolRef` -> `SymtabEntry`ラッパーメソッドを生成する便利なヘルパーマクロについては、`@derefmethod`マクロを参照してください。利用可能なAPI操作のリストは以下に示されており、サブクラスが実装する必要のあるメソッドは強調表示されています。

### 作成:

  * *SymtabEntry()*

### ユーティリティ:

  * deref()

### プロパティ:

  * *symbol_name()*
  * *symbol_value()*
  * *isundef()*
  * *isglobal()*
  * *islocal()*
  * *isweak()*
