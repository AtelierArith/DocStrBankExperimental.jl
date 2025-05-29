```
bitarray(v::Vector, [nbits::Int]) -> BitArray
bitarray(v::Int, nbits::Int) -> BitArray
bitarray(nbits::Int) -> Function
```

整数ベクトルからBitArrayを構築します。nbitsが指定されていない場合、デフォルトは64です。整数が指定された場合、Vector/Intをbitarrayにマッピングする関数を返します。
