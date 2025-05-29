```
gatherdofnums!(self::F, dest::A, conn::CC) where {F<:AbstractField, A, CC}
```

フィールドからdofnumsを収集します。

順序は次のとおりです：接続性の各ノードについて、そのノードのすべての自由度をバッファにコピーし、次のノードに進みます。
