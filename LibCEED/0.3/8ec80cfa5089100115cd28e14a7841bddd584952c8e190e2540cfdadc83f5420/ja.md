```
Context(ceed::Ceed, data; mtype=MEM_HOST, cmode=USE_POINTER)
```

ユーザーQ関数が任意のデータオブジェクトにアクセスできる`CeedQFunctionContext`オブジェクトを作成します。`data`は可変構造体のインスタンスである必要があります。コピー方式`cmode`が`USE_POINTER`の場合、データは`set_context!`を使用して`QFunction`オブジェクトに割り当てられたときにGCから保持されます。

コピー方式`OWN_POINTER`はこのインターフェースではサポートされていません。なぜなら、Juliaで割り当てられたオブジェクトはCから解放できないからです。
