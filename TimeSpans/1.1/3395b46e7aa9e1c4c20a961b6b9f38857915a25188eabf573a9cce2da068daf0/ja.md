```
istimespan(x)
```

`x`が`TimeSpans.start(x)`および`TimeSpans.stop(x)`をサポートするように宣言されている場合は`true`を返し、それ以外の場合は`false`を返します。

`TimeSpans.start`/`TimeSpans.stop`をオーバーロードする型は、`istimespan`もオーバーロードする必要があります。
