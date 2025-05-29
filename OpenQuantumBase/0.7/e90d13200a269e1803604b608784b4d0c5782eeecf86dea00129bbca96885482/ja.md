```
function (h::DenseHamiltonian)(s::Real)
```

ハミルトニアンを呼び出すと、値 $2πH(s)$ が返されます。引数 `s` は（無次元の）時間です。返される行列は角周波数の単位です。
