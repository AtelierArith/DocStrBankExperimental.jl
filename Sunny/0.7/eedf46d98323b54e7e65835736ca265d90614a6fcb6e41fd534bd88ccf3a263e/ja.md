```
Units(energy, length)
```

参照 `energy` および `length` スケールの単位における物理定数。可能な長さは `[:angstrom, :nm]` です。原子スケールのモデリングでは、CIFファイル標準に従って `length=:angstrom` の単位で作業することが望ましいです。可能なエネルギー単位は `[:meV, :K, :THz, :inverse_cm, :T]` です。ケルビンはボルツマン定数 $k_B$ を介してエネルギーに変換されます。同様に、ヘルツはプランク定数 $h$ を介して、逆センチメートルは光速 $c$ を介して、テスラ（磁場強度）はボーア磁子 $μ_B$ を介して変換されます。特定の `Units` システムに対して、上記にリストされた任意の長さおよびエネルギースケールのシンボルにアクセスできます。

# 例

```julia
# [energy] = meV および [length] = Å の単位系
units = Units(:meV, :angstrom)

# ボルツマン定数 kB を使用して 1 ケルビンを meV に変換
@assert units.K ≈ 0.0861733326

# プランク定数 h を使用して 1 THz を meV に変換
@assert units.THz ≈ 4.135667696

# 定数 h c を使用して 1 cm⁻¹ を meV に変換
@assert units.inverse_cm ≈ 0.1239841984

# ボーア磁子 μB を使用して 1 テスラを meV に変換
@assert units.T ≈ 0.05788381806

# 単位 Å³ meV における物理定数 μ0 μB²。
@assert u.vacuum_permeability ≈ 0.6745817653
```
