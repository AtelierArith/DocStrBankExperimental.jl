```
function AdiabaticFrameHamiltonian(ωfuns, geofuns)
```

断熱フレームハミルトニアンのコンストラクタ。`ωfuns`はハミルトニアンの固有エネルギー（`GHz`単位）を指定する1次元配列の関数です。`geofuns`はハミルトニアンの幾何学的位相を指定する1次元配列の関数です。`geofuns`は、列優先順序で対角要素を含まないフラットな下三角行列と考えることができます。
