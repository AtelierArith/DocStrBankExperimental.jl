```
dates(var::OutputVar)
```

`var`の`date`次元を返します。

`dates`が次元であれば、それを返します。

そうでない場合は、`start_date`と`times`から日付を計算しようとします。この場合、`times`は秒であると仮定します。
