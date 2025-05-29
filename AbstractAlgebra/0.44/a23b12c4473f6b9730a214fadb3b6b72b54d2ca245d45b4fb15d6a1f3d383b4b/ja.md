```
inv(M::MatrixElem{T}) where {T <: RingElement}
```

非特異な $n\times n$ 行列 $M$ が環上にあるとき、$MX = I_n$ となる $n\times n$ 行列 $X$ を返します。ここで、$I_n$ は $n\times n$ 単位行列です。もし $M$ が基底環上で逆行列を持たない場合、例外が発生します。
