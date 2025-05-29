```
divides(a::AbsSimpleNumFieldElem, b::AbsSimpleNumFieldElem)
```

$ b $ が $ a $ を割り切る場合は `true` に設定されるフラグと、$ a = bh $ となる数体要素 $ h $ からなるペアを返します。存在しない場合、$ h $ の値は不確定です。
