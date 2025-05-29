```
@spectra [expr=BlockSpectralMatrix]
```

ブロックベクトルを展開します。これは、すべてのサブブロックに対して `getblock` を呼び出し、それらをタプルに入れることと同等です。

# 例

```julia
# マスクalmからスタックされたEE,BBモード結合行列を計算する
M_EE_BB = mcm(:EE_BB, map2alm(mask1), map2alm(mask2))
# スタックされたEEおよびBBスペクトルに2×2ブロックモード結合行列を適用する
@spectra Cl_EE, Cl_BB = M_EE_BB \ [pCl_EE; pCl_BB]
```
