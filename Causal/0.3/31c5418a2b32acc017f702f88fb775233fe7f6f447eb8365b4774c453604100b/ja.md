```julia
approve!(comp)

```

`comp`の`handshake`リンクを読み取ります。承認されていない場合や`handshake`リンクから`false`が読み取られた場合、`comp`がステップを踏んでいる間に`comp`の`trigger`リンクのために起動されたタスクがスタックします。
