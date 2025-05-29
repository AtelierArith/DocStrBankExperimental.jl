```
選択
```

この構造は、文字列の選択をクエリ呼び出しへの呼び出しに変換することによって、典型的なJuliaフィルタリング関数内で使用されるときに関数として機能します。

# 例

文字列を使用して最初の残基のCA原子を選択する：

```jldoctest
julia> using PDBTools

julia> atoms = read_pdb(PDBTools.TESTPDB, "protein");

julia> findfirst(Select("name CA"), atoms)
5

julia> filter(Select("name CA and residue 1"), atoms)
   Vector{Atom{Nothing}} with 1 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       5   CA     ALA     A        1        1   -8.483  -14.912   -6.726  1.00  0.00     1    PROT         5

```
