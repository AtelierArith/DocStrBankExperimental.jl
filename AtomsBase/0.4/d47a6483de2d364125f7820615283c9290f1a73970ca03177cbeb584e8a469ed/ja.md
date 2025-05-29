化学種をエンコードするために、原子番号、陽子の数、および追加の未指定情報を表す整数を `UInt32` としてラップします。

標準化学元素のコンストラクタ

```julia
ChemicalSpecies(Z::Integer)
ChemicalSpecies(sym::Symbol) 
# 例えば 
ChemicalSpecies(:C)
ChemicalSpecies(6)
```

同位体のコンストラクタ 

```julia
# 標準的な炭素 = C-12
ChemicalSpecies(:C)
ChemicalSpecies(:C; n_neutrons = 6)

# C-13 のための3つの同等のコンストラクタ
ChemicalSpecies(:C; n_neutrons = 7)
ChemicalSpecies(6; n_neutrons = 7)
ChemicalSpecies(:C13)
# 重水素
ChemicalSpecies(:D) 
```
