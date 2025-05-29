```
kernel(M::SMat{T}; side::Symbol = :left) where {T <: FieldElement}
```

行列 $N$ を返し、$M$ のカーネルの基底を含みます。`side` が `:left`（デフォルト）の場合、左カーネルが計算されます。つまり、左カーネル空間を与える行の行列です。`side` が `:right` の場合、右カーネルが計算されます。つまり、右カーネル空間を与える列の行列です。
