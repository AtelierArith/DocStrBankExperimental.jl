```
Bits(input::Integer)
Bits{T}(input::Integer)
Bits{T}(input)
```

`input`として渡されたビットから`Bits`を構築します。これは`Integer`として、または配列やその他の一般的な反復可能なものから渡すことができます。基本的には、`input`のビットへのビューであり、ベクトルのような構文を使用して操作することができます。
