```
Smartphore( size )
```

`size` の同時使用を許可するカウントセマフォを作成します。Base Semaphore 呼び出しとの唯一の違いは、Smartphores がどの許可 ID を受け取ったかを教えてくれることです。これは、例えば、`size` ビットの事前予約されたメモリを共有する場合に役立ちます。

各 acquire は release と対になっている必要があります。これにより、acquire/release 呼び出しに対して acquire & release メモリ順序が提供されます。
