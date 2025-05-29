```
foldp(f, init, inputs...)
```

過去の値に対して[フォールド](http://en.wikipedia.org/wiki/Fold_(higher-order_function))します。

入力信号が変化するにつれて値を蓄積します。`init`はアキュムレーターの初期値です。`f`は`1 + length(inputs)`個の引数を取るべきです：最初の引数は現在の蓄積された値で、残りは現在の入力信号の値です。`f`は`inputs`の1つ以上が更新されると呼び出されます。次の蓄積された値を返す必要があります。
