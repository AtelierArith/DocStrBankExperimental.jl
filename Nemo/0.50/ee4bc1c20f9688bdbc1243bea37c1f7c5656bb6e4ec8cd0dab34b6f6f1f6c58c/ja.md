```
inv(x::ComplexMatrix)
```

与えられた $n\times n$ 型 `AcbMatrix` の行列に対して、$AX$ が単位行列を含むような $n\times n$ 行列 $X$ を返します。もし $A$ が数値的に逆転できない場合は、例外が発生します。
