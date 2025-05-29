```
kernel(f::ModuleHomomorphism{T}) where T <: RingElement
```

与えられたモジュール準同型 $f$ のカーネルオブジェクト $K$（その定義域の部分モジュールとして）と、カーネルから $f$ の定義域への標準的な注入を含むペア `K, g` を返します。
