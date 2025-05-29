```
解像度
```

EDS検出器の解像度のチャネル依存性を説明する抽象型です。

実装：

```
resolution(eV::Float64, res::Resolution)::Float # 指定されたエネルギーでの解像度
profile(energy::Float64, xrayE::Float64, res::Resolution) # 指定されたエネルギーでの信号の振幅
extent(xrayE::Float64, res::Resolution, ampl::Float64)::Tuple{2,Float} # 信号がamplを超えるチャネルの範囲
```
