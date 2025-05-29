```
residue_residue_distance(
    r1::PDBTools.Residue, 
    r2::PDBTools.Residue; 
    positions::AbstractVector{AbstractVector{T}}=nothing; 
    unitcell=nothing
)
```

タンパク質構造内の2つの残基間の最小距離を計算します。`positions`引数が提供されていない場合、関数は残基内の原子の座標を使用して距離を計算します。`positions`が提供されている場合、関数は位置配列内の座標を使用します。

# 引数

  * `r1::PDBTools.Residue`: 残基1
  * `r2::PDBTools.Residue`: 残基2
  * `positions::AbstractVector{AbstractVector{T}}`: 構造内の原子のオプションの代替位置。
  * `unitcell=nothing`: 周期境界条件のためのオプションの単位セル寸法。

!!! note
    残基内の原子のインデックスは、位置配列内の原子のインデックスと一致する必要があります。


# 例

```jldoctest
julia> using PDBTools

julia> ats = read_pdb(PDBTools.DIMERPDB);

julia> residues = collect(eachresidue(ats));

julia> r1 = residues[1]; r10 = residues[10];

julia> println(name(r1), resnum(r1), " and ", name(r10), resnum(r10))
LYS211 and GLU220

julia> d = residue_residue_distance(r1, r10)
16.16511f0
```
