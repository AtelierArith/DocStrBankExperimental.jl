```
TxOut
```

Each output spends a certain number of satoshis, placing them under control of anyone who can satisfy the provided pubkey script. A `TxOut` is composed of

  * `value::UInt64`, number of satoshis to spend. May be zero; the sum of all

outputs may not exceed the sum of satoshis previously spent to the outpoints provided in the input section. (Exception: coinbase transactions spend the block subsidy and collected transaction fees.)

  * `scriptpubkey::Script` which defines the conditions which must be

satisfied to spend this output.
