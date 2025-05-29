```
significance(signal, bkg) -> `(significance, error_on_significance)`
```

信号と背景のヒストグラムの有意性を計算します。この関数は、単純な `S / sqrt(B)` よりも正確なアルゴリズムを使用します。

Ref: https://cds.cern.ch/record/2736148/files/ATL-PHYS-PUB-2020-025.pdf

## 例:

```julia
h1 = Hist1D(rand(1000);  binedges = [0, 0.5])
h2 = Hist1D(rand(10000); binedges = [0, 0.5]);

julia> s1 = significance(h1,h2)
(6.738690967342175, 0.3042424717261312)
```
