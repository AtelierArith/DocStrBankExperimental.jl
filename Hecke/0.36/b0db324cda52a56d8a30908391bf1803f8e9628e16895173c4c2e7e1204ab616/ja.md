```
AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}(O::AbsSimpleNumFieldOrder, a::ZZMatrix) -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}

$O$の基底行列$a$を持つイデアルを作成します。
サニティチェックはありません。データはコピーされず、$a$はもう使用しないでください。
```

AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}(a::ZZRingElem, b::AbsSimpleNumFieldOrderElem) -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}

```
$b$のイデアル$(a,b)$を作成します。
サニティチェックはありません。データはコピーされず、$a$と$b$はもう使用しないでください。
```

AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}(O::AbsSimpleNumFieldOrder, a::ZZRingElem, b::AbsSimpleNumFieldElem) -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}

```
$O$のイデアル$(a,b)$を作成します。
サニティチェックはありません。データはコピーされず、$a$と$b$はもう使用しないでください。
```

AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}(x::AbsSimpleNumFieldOrderElem) -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}

```
$O$のイデアル$(x)$を作成します。
サニティチェックはありません。データはコピーされず、$x$はもう使用しないでください。
```
