```
pseudo_matrix(m::Generic.Mat{AbsSimpleNumFieldOrderElem}, c::Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> PMat{AbsSimpleNumFieldElem, AbsSimpleNumFieldOrderFractionalIdeal}
```

$$
Z_k
$$

-モジュール $\sum c_i m_i$ を表す（行）擬似行列を返します。ここで、$c_i$ は $c$ のイデアルであり、$m_i$ は $M$ の行です。
