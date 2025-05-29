```
read_pdb(pdbfile::String, selection::String)
read_pdb(pdbfile::String; only::Function = all)

read_pdb(pdbdata::IOBuffer, selection::String)
read_pdb(pdbdata::IOBuffer; only::Function = all)
```

PDBファイルを読み込み、データを`Atom`型のベクターに格納します。

選択が提供された場合、選択に一致する原子のみが読み込まれます。たとえば、`resname ALA`は残基ALA内のすべての原子を選択します。

`only`関数キーワードが提供された場合、`only(atom)`がtrueである原子のみが読み込まれます。

### 例

```jldoctest
julia> using PDBTools

julia> protein = read_pdb(PDBTools.TESTPDB)
   Vector{Atom{Nothing}} with 62026 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     ALA     A        1        1   -9.229  -14.861   -5.481  0.00  0.00     1    PROT         1
       2  HT1     ALA     A        1        1  -10.048  -15.427   -5.569  0.00  0.00     1    PROT         2
⋮
   62025   H1    TIP3     C     9339    19638   13.218   -3.647  -34.453  1.00  0.00     1    WAT2     62025
   62026   H2    TIP3     C     9339    19638   12.618   -4.977  -34.303  1.00  0.00     1    WAT2     62026

julia> ALA = read_pdb(PDBTools.TESTPDB,"resname ALA")
   Vector{Atom{Nothing}} with 72 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     ALA     A        1        1   -9.229  -14.861   -5.481  0.00  0.00     1    PROT         1
       2  HT1     ALA     A        1        1  -10.048  -15.427   -5.569  0.00  0.00     1    PROT         2
⋮
    1339    C     ALA     A       95       95   14.815   -3.057   -5.633  1.00  0.00     1    PROT      1339
    1340    O     ALA     A       95       95   14.862   -2.204   -6.518  1.00  0.00     1    PROT      1340

julia> ALA = read_pdb(PDBTools.TESTPDB, only = atom -> atom.resname == "ALA")
   Vector{Atom{Nothing}} with 72 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     ALA     A        1        1   -9.229  -14.861   -5.481  0.00  0.00     1    PROT         1
       2  HT1     ALA     A        1        1  -10.048  -15.427   -5.569  0.00  0.00     1    PROT         2
⋮
    1339    C     ALA     A       95       95   14.815   -3.057   -5.633  1.00  0.00     1    PROT      1339
    1340    O     ALA     A       95       95   14.862   -2.204   -6.518  1.00  0.00     1    PROT      1340
```
