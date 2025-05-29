```
concat(a, b)
concat(a, bvconst(0xffff, 16), b, bvconst(0x01, 8), ...)
concat(bvconst(0x01, 8), bvconst(0x02, 12)...)
```

ビットベクター式と異なるサイズの定数を連結します。定数が正しいビットサイズであることを保証するためには、bvconstでラップする必要があります。そうでない場合、そのサイズは`bitcount`を使用して推測されます。

concat(a,b)は、サイズがa.length + b.lengthのビットベクターを返します。

引数は、concatへの最初の引数が結果の値の最上位ビットに対応するように連結されます。したがって：

```julia
    expr = concat(bvconst(0x01, 8), bvconst(0x02, 8), bvconst(0x03, 4))
    println(expr.length) # 20
    println(expr.value) # 0x01023
```
