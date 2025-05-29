```
HCubatureJL(; norm=norm, initdiv=1)
```

HCubature.jlによる多次元「h適応」積分。このメソッドは、オプションの引数`initdiv`と`norm`も受け取ります。これらは、それぞれ積分領域の各次元が分割される初期セグメント数と、誤差を計算するためのノルムです。

## 参考文献

@article{genz1980remarks, title={Remarks on algorithm 006: An adaptive algorithm for numerical integration over an N-dimensional rectangular region}, author={Genz, Alan C and Malik, Aftab Ahmad}, journal={Journal of Computational and Applied mathematics}, volume={6}, number={4}, pages={295–302}, year={1980}, publisher={Elsevier} }
