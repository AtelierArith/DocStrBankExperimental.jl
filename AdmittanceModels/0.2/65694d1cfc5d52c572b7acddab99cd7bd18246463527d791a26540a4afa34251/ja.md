```
lossless_modes_sparse(pso::PSOModel; num_modes=1, maxiter=200)
```

スパース一般化固有値ソルバーを使用して、損失を無視してPSOModelの`num_modes`最低周波数モードを見つけます。各モードは固有値`λ`と固有ベクトル`v`で構成されます。モードの周波数は`imag(λ)/(2π)`であり、減衰率は`-2*real(λ)/(2π)`です。
