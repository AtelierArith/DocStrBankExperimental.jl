```
TxIn
```

Each non-coinbase input spends an outpoint from a previous transaction. A `TxIn` is composed of

  * `prevout::Outpoint`, The previous outpoint being spent
  * `scriptsig::Vector{UInt8}`, which satisfies the conditions placed in

the outpoint’s pubkey script. Should only contain data pushes

  * `sequence::UInt32` number. Default for Bitcoin Core and almost all other

programs is `0xffffffff`
