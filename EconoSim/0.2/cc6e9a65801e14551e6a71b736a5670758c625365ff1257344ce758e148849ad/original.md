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

Queues a transfer to be executed later. The transfer is queued in the source balance.
