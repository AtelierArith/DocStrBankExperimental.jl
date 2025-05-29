```
etale_algebra_structures(X::Object)
etale_algebra_structures(X::Object, unit::Morphism)
```

$$
X
$$

上の可分代数オブジェクトの集合を返します。代数構造が存在しない場合は空の配列が返されます。代数が連結でない場合、すなわち$Hom(𝟙,X) ≠ k$の場合は、単位を提供する必要があります。
