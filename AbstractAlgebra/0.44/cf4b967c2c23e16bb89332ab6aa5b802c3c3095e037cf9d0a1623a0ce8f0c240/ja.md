```
sqrt(a::ResFieldElem{T}; check::Bool=true) where T <: Integer
```

$ a $ の平方根を返します。デフォルトでは、入力が平方でない場合、関数は例外をスローします。`check=false` の場合、このテストは省略されます。
