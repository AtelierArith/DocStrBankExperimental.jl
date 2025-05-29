```
dtpool(name)
```

カーネルプール変数に関するデータを返します。

### 引数

  * `name`: 値を返す変数の名前

### 出力

タプル `(n ,vartype)` を返します。

  * `n`: 名前に対して返される値の数
  * `vartype`: 変数の型

      * `:C` はデータが文字データである場合
      * `:N` はデータが数値である場合
      * `:X` はプールに変数名が存在しない場合

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dtpool_c.html)
