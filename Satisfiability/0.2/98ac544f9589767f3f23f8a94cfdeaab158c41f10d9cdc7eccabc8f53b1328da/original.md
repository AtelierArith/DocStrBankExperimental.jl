```
bvconst(0x01, 32)
bvconst(2, 8)
```

Wraps a nonnegative integer constant for interoperability with BitVectorExprs. While the correct size of a BitVector constant can usually be inferred (for example, if `a` is a BitVector of length 16, the constant in `a + 0x0f` can also be wrapped to length 16), in a few cases it cannot.

Specifically, when concatenating BitVectorExprs and constants, one should wrap the constants in `bvconst` to ensure their size matches your expectations.

`bvconst` will pad constants to the requested size, but will not truncate constants. For example, `bvconst(0xffff, 12)` yields an error because `0xffff`` requires 16 bits.
