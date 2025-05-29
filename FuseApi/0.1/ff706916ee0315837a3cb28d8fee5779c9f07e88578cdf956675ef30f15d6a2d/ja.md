```
FuseCmdlineArgs <: Layout
```

fuse*parse*cmdlineに渡すためのコマンドライン引数のレイアウトテンプレート

`argv`が指すベクターの長さは、フィールド`argc`に格納されます。フィールド`allocated`は、データがJulia生成の場合は`0`に設定する必要があります。

Juliaによって生成された場合は、`CStructGuarded{FuseCmdlineArgs}`を使用してください。
