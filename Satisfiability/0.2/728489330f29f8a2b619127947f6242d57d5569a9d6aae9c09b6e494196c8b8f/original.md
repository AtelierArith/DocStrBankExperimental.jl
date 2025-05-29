```
concat(a, b)
concat(a, bvconst(0xffff, 16), b, bvconst(0x01, 8), ...)
concat(bvconst(0x01, 8), bvconst(0x02, 12)...)
```

Concatenate BitVectorExprs and constants of varying sizes. To guarantee a constant is the correct bit size, it should be wrapped using bvconst - otherwise its size will be inferred using `bitcount`.

concat(a,b) returns a BitVector with size a.length + b.length.

Arguments are concatenated such that the first argument to concat corresponds to the most significant bits of the resulting value. Thus:

```julia
    expr = concat(bvconst(0x01, 8), bvconst(0x02, 8), bvconst(0x03, 4))
    println(expr.length) # 20
    println(expr.value) # 0x01023
```
