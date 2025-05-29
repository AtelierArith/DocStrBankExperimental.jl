化学種をエンコードするために、原子番号、陽子の数、および最大4文字の追加名を表す整数をラップします。

name変数は、PDB形式の原子名として使用するか、同じ種類の原子を互いに区別するための他の方法として使用できます。

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
# 標準の炭素 = C-12
ChemicalSpecies(:C)
ChemicalSpecies(:C; n_neutrons = 6)

# C-13のための3つの同等のコンストラクタ
ChemicalSpecies(:C; n_neutrons = 7)
ChemicalSpecies(6; n_neutrons = 7)
ChemicalSpecies(:C13)
# 重水素
ChemicalSpecies(:D)
```

名前のためのコンストラクタ

```julia
ChemicalSpecies(:C; atom_name=:MyC)
ChemicalSpecies(:C13; atom_name=:MyC)
```

異なる同位体と名前との比較

```julia
# 真
ChemicalSpecies(:C13) == ChemicalSpecies(:C)

# 偽
ChemicalSpecies(:C12) == ChemicalSpecies(:C13)

# 真
ChemicalSpecies(:C; atom_name=:MyC) == ChemicalSpecies(:C)

# 真
ChemicalSpecies(:C12; atom_name=:MyC) == ChemicalSpecies(:C12)

# 偽
ChemicalSpecies(:C; atom_name=:MyC) == ChemicalSpecies(:C12)

# 真
ChemicalSpecies(:C12; atom_name=:MyC) == ChemicalSpecies(:C)

# 真
ChemicalSpecies(:C; atom_name=:MyC) == ChemicalSpecies(:C12; atom_name=:MyC)
```
