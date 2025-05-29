```
xor(z1,...,zn)
⊻(z1,...zn)
```

XOR (exclusive or) is true if exactly one of z1,...,zn is true and false otherwise. Use dot broadcasting across arrays.

Special cases:

  * `xor(z)` returns `z`.
  * `xor(false, z)` returns `z`.
  * `xor(true, z)` returns `¬z`.
  * `xor(true, true, z)` returns `false`.
