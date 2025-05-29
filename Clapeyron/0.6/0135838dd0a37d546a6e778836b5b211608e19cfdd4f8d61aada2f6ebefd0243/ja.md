```
ZeroResidual <: EoSModel
ZeroResidual(components; 
idealmodel = BasicIdeal,
ideal_userlocations = String[],
verbose = false)
```

## 入力パラメータ

なし

## 説明

ゼロ残差モデル。

```
    a_res(model,V,T,z) = 0
```
