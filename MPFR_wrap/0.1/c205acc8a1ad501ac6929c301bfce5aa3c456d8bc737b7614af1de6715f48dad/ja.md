```
dim!(rop, op1, op2, rnd)
```

`rop`を`op1`と`op2`の正の差に設定します。すなわち、`op1−op2`を`op1>op2`の場合は`rnd`の方向に丸め、`op1≤op2`の場合は+0を設定し、`op1`または`op2`がNaNの場合はDomainErrorをスローします。
