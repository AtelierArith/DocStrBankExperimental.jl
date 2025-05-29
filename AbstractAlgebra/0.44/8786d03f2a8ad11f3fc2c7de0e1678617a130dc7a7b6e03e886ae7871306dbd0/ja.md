```
Base.sqrt(f::PolyRingElem{T}; check::Bool=true) where T <: RingElement
```

$$
f
$$

の平方根を返します。デフォルトでは、関数は入力が平方であることを確認し、そうでない場合は例外を発生させます。`check=false`の場合、このチェックは省略されます。
