```
isequal(x::ZZLaurentSeriesRingElem, y::ZZLaurentSeriesRingElem)
```

$ x == y $ が正確に等しい場合は `true` を返し、それ以外の場合は `false` を返します。この関数によって等しいと宣言されるのは、冪級数が正確に同じで、同じ精度である場合のみです。
