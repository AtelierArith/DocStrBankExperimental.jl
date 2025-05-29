```
calibrationReport(E, Ecal, codata::Codata; unitIn="Hartree", msg=true)
```

エネルギー E とキャリブレーション値 Ecal の比較

デフォルト入力: Hartree

#### 例:

```
julia> codata = castCodata(2022)
julia> calibrationReport(1.1, 1.0, codata; unitIn="Hartree")

キャリブレーションレポート (Float64):
Ecal = 1 Hartree
E = 1.1000000000000001 Hartree
絶対精度: ΔE = 0.1 Hartree (657.968 THz)
相対精度: ΔE/E = 0.0909091
```
