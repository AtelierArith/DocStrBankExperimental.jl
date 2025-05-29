```
z(mat::Material) = z(Donovan2002, mat)
z(::Type{NaiveZ|ElectronFraction|AtomicFraction}, mat::Material)
z(::Type{ElasticFraction}, mat::Material, e::AbstractFloat)
z(::Type{Donovan2002}, mat::Material; exponent=0.667)
```

材料の平均原子番号を計算します。

```
アルゴリズム:
  * NaiveZ - 質量分率平均
  * AtomFraction - 原子分率平均
  * ElectronFraction - 単純電子分率平均
  * ElasticFraction - 散乱断面積平均
  * Donovan2002 - Yukawa/Donovan修正指数電子分率平均
```

詳細については、J.J. Donovan, N.E. PingitoreによるMean Zアルゴリズムを参照してください。Microsc. Microanal. 2002 ; 8 , 429（また、Microsc. Microanal. 27 (Suppl 1), 2021も参照）
