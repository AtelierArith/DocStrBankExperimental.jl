```
`ThreeDGrid`を`dev`ice上に構築します; デフォルトでは`CPU()`上です。グリッドサイズは`Lx`、`Ly`、`Lz`、解像度は`nx`、`ny`、`nz`で、最も左の位置は`x0`、`y0`、`z0`です。FFTプランは、FFTWフラグ`effort`を使用して`nthreads` CPUのために生成されます。浮動小数点型は`T`です。`aliased_fraction`キーワードは、`dealias!`関数によってゼロにされる最高の波数を決定します; 1/3は二次非線形性のための標準値です。
```
