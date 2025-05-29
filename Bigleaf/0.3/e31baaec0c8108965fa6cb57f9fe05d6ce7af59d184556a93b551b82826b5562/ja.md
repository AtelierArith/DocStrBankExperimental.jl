```
Rg_to_PPFD(Rg,J_to_mol=4.6,frac_PAR=0.5)
PPFD_to_Rg(PPFD,J_to_mol=4.6,frac_PAR=0.5)
```

全球放射（W m-2）と光合成光子フラックス密度（umol m-2 s-1）間の変換

# 引数

  * Rg:       全球放射 = 表面での入射短波放射（W m-2）
  * PPFD:     光合成光子フラックス密度（umol m-2 s-1）
  * J*to*mol: J m-2 s-1（= W m-2）からumol（量子）m-2 s-1への変換係数
  * frac_PAR: 入射太陽放射のうち光合成活性放射（PAR）である割合；デフォルトは0.5

# 詳細

変換は次のように与えられます：

$$
PPFD = Rg * frac_PAR * J_to_mol
$$

デフォルトでは、結合変換係数（`frac_PAR * J_to_mol`）は2.3です。

# 例

```@example
# 測定された入射短波放射500 Wm-2を
# PPFD（umol m-2 s-1）に変換し、逆に変換する
Rg_to_PPFD(500)
PPFD_to_Rg(1150)
```
