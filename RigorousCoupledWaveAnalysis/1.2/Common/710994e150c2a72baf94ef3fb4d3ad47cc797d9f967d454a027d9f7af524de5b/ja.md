```
ngrid(Nx,Ny,use_cude=false)
```

平面波展開の次数 n を計算します

# 引数

  * `Nx` : x の最大次数
  * `Ny` : y の最大次数
  * `use_cuda` : オプション、CUDA GPU ソルバーに切り替え

# 出力

  * `nx` : x の次数
  * `ny` : y の次数
  * `dnx` : x の微分次数
  * `dny` : y の微分次数
