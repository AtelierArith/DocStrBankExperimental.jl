```
memchr(x, bytes)
memchr(ptr::Ptr, len::UInt, bytes)
```

`bytes`の中の任意のバイトの最初の位置をメモリ`mem`から返します。バイトが見つからなかった場合は`nothing`を返します。

`bytes`は`Val{::ByteSet}`であることができ、その場合、この関数はバイトセットに特化します。または、単一の`UInt8`であることもでき、その場合は特化しません。

`x`は`pointer`と`sizeof`を実装する任意の型であるか、またはポインタとメモリの長さを渡すことができます。
