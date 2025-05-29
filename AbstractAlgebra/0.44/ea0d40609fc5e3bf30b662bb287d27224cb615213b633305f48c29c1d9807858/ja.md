```
pseudo_inv(M::MatrixElem{T}) where {T <: RingElement}
```

非特異な $n\times n$ 行列 $M$ が与えられたとき、$X$ と $d$ からなるタプルを返します。ここで、$X$ は $n\times n$ 行列、$d$ は分母であり、$MX = dI_n$ となるようにします。ここで、$I_n$ は $n\times n$ 単位行列です。分母は $M$ の行列式の符号を考慮したものになります。もし $M$ が特異であれば、例外が発生します。
