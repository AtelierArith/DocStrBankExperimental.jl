```
next_address!(wallet::AbstractDeterministicWallet)::AbstractPublicKey
```

Produce the next address in the deterministic wallet. This should be the first value in the pair produced from `next_keypair!(wallet)`.
