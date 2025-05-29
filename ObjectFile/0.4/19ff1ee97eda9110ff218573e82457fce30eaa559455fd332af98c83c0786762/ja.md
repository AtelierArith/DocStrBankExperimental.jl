```
SymbolRef
```

`SymtabEntry`への参照と、この`SymtabEntry`がどの`ObjectHandle`から来ているかの参照を提供します。これは、ユーザーがオブジェクトファイル内のシンボルと対話するための主な方法であるべきです。利用可能なAPI操作のリストは以下に示されており、サブクラスが実装しなければならないメソッドは強調表示されています。これは`SymtabEntry`オブジェクトAPIと重複していることに注意してください。これは、多くのメソッドが使いやすさのために基盤となる`SymtabEntry` API呼び出しへの単なるパススルーであるため、意図的なものです。

### 作成:

  * *SymbolRef()*

### ユーティリティ:

  * *deref()*
  * *Symbols()*
  * handle()

### プロパティ:

  * *symbol_number()*
  * *symbol_name()*
  * symbol_value()
  * isundef()
