```
isempty(a::MatrixElem{T}) where T <: NCRingElement
```

`a` にエントリが含まれていない場合（すなわち `length(a) == 0`）、`true` を返し、それ以外の場合は `false` を返します。
