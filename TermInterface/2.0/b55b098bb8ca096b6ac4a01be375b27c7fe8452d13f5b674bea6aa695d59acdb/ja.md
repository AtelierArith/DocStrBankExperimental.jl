```
arguments(x)
```

関数呼び出し式における関数呼び出しの引数を返します。`iscall(x)`が真である必要があります。

`x`の型と内部表現に応じて、`arguments(x)`は非決定的に未ソートのコレクションを返す場合があります。これは、引数の順序が重要でないが、操作の速度が重要な場合に、式の引数を取得することを保証するためです。引数をソートされた方法で取得することを保証するには、`sorted_arguments`関数を使用して実装することができます。
