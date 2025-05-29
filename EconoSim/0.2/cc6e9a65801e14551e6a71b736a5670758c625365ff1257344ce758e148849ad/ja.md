```
queue_transfer!(balance1::Balance,
            type1::EntryType,
            balance2::Balance,
            type2::EntryType,
            entry::BalanceEntry,
            amount::Real,
            timestamp::Integer = 0;
            comment::String = "")
```

後で実行される転送をキューに追加します。転送はソースバランスにキューされます。
