```
badkpv(caller, name, comp, size, divby, typ)
```

カーネルプール変数が存在するかどうか、存在する場合は正しいサイズとタイプを持っているかどうかを判断します。

### 引数

  * `caller`: このルーチンを呼び出しているルーチンの名前
  * `name`: カーネルプール変数の名前
  * `comp`: 比較演算子
  * `size`: カーネルプール変数の期待されるサイズ
  * `divby`: カーネルプール変数のサイズの除数
  * `type`: カーネルプール変数の期待されるタイプ

### 出力

この関数は、カーネルプール変数が正常であれば `false` を返し、そうでない場合は例外がスローされます。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/badkpv_c.html)
