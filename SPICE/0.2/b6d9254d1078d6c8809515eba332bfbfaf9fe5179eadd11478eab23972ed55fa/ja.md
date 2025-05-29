```
bodfnd(body, item)
```

カーネルプール内の任意のボディに対して、特定のアイテムの値が存在するかどうかを判断します。

### 引数

  * `body`: ボディのIDコード
  * `item`: 検索するアイテム（`"RADII"`、`"NUT_AMP_RA"`など）

### 出力

アイテムがカーネルプールに存在する場合は `true` を返し、存在しない場合は `false` を返します。

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/bodfnd_c.html)
