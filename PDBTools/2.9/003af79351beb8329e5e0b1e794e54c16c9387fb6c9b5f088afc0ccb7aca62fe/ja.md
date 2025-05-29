```
read_mmcif(mmCIF_file::String, selection::String; field_assignment)
read_mmcif(mmCIF_file::String; only::Function = all, field_assignment)

read_mmcif(mmCIF_data::IOBuffer, selection::String; field_assignment)
read_mmcif(mmCIF_data::IOBuffer; only::Function = all, field_assignment)
```

mmCIFファイルを読み込み、データを`Atom`型のベクターに格納します。

ファイル名以外のすべてのフィールドはオプションです。

選択が提供されると、選択に一致する原子のみが読み込まれます。たとえば、`resname ALA`は残基ALA内のすべての原子を選択します。

`only`関数キーワードが提供されると、`only(atom)`がtrueである原子のみが返されます。

`field_assignment`キーワードは`nothing`（デフォルト）または`Dict{String,Symbol}`であり、mmCIFファイル内のどのフィールドを`Atom`型に読み込むかを指定するために使用できます。たとえば、`field_assignment = Dict("type_symbol" => :name)`は、mmCIFファイル内の`_atom_site.type_symbol`フィールドを`Atom`型の`name`フィールドに読み込みます。

デフォルトの割り当ては、標準のmmCIF規約に従います：

```julia
Dict{String,Symbol}(
    "id" => :index_pdb
    "Cartn_x" => :x
    "Cartn_y" => :y
    "Cartn_z" => :z
    "occupancy" => :occup
    "B_iso_or_equiv" => :beta
    "pdbx_formal_charge" => :charge
    "pdbx_PDB_model_num" => :model
    "label_atom_id" => :name
    "label_comp_id" => :resname
    "label_asym_id" => :chain
    "auth_seq_id" => :resnum
    "type_symbol" => :pdb_element
)
```

出典: https://mmcif.wwpdb.org/docs/tutorials/content/atomic-description.html

### 例

```jldoctest
julia> using PDBTools

julia> ats = read_mmcif(PDBTools.TESTCIF)
   Vector{Atom{Nothing}} with 76 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     GLY     A        1        1   -4.564   25.503   24.113  1.00 24.33     1                 1
       2   CA     GLY     A        1        1   -4.990   26.813   24.706  1.00 24.29     1                 2
⋮
      75    O     HOH     Q       63       15   -3.585   34.725   20.903  1.00 19.82     1              2980
      76    O     HOH     Q       64       16   -4.799   40.689   37.419  1.00 20.13     1              2981

julia> ats = read_mmcif(PDBTools.TESTCIF, "index < 3")
   Vector{Atom{Nothing}} with 2 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     GLY     A        1        1   -4.564   25.503   24.113  1.00 24.33     1                 1
       2   CA     GLY     A        1        1   -4.990   26.813   24.706  1.00 24.29     1                 2

julia> ats = read_mmcif(PDBTools.TESTCIF; only = at -> name(at) == "CA")
   Vector{Atom{Nothing}} with 11 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       2   CA     GLY     A        1        1   -4.990   26.813   24.706  1.00 24.29     1                 2
       6   CA     GLN     A        2        2   -4.738   30.402   23.484  1.00 23.74     1                 6
⋮
      70   CA      CA     G     1003       10  -24.170   27.201   64.364  1.00 27.40     1              2967
      71   CA      CA     H     1004       11  -10.624   32.854   69.292  1.00 29.53     1              2968

```
