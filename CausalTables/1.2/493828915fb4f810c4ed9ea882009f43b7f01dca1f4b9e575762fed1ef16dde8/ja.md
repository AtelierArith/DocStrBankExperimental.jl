```
parents(o::CausalTable, symbol)
```

`symbol`の因果的に前にある変数をCausalTable `o`から選択します。これは`causes`属性に基づいています。`symbol`が`o.causes`に含まれていない場合、この関数は空の`CausalTable`を出力します。

# 引数

  * `o::CausalTable`: `symbol`の親変数を抽出するための`CausalTable`オブジェクト。
  * `symbol`: 親変数を抽出するための変数。

# 戻り値

`symbol`の親のみを含む新しい`CausalTable`
