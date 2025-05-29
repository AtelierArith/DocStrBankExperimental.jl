```
automorphism_list(C::CyclotomicExt; gens::Vector{NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}}) -> Vector{NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}}
```

サイクリック拡張によって定義された絶対体の自己同型を計算します。すなわち、`absolute_simple_field(C)`の自己同型です。基底体が正規であることを前提としています。`gens`は、$C$の基底体の自己同型群の生成元の集合でなければなりません。
