```
@optinode(optigraph, expr...)
```

`optigraph`に新しいoptinodeを追加します。式`expr`は次のいずれかの形式であることができます。

  * `nodename`の形式で、変数名`varname`を持つ単一のoptinodeを作成します。
  * `nodename[...]`または`[...]`の形式で、JuMPコンテナを使用してoptinodeのコンテナを作成します。
