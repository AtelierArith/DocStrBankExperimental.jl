```
printatom(atom::Atom)
printatom(io::IO, atom::Atom)
```

`Atom` 構造体を人間が読みやすい形式で、タイトル行と共に出力します。デフォルトでは出力は `stdout` に印刷され、`io` 引数を使用して別の出力ストリームを指定できます。

### 例

```jldoctest
julia> using PDBTools

julia> atoms = read_pdb(PDBTools.TESTPDB, "protein and residue 2");

julia> printatom(atoms[1])
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
      13    N     CYS     A        2        2   -6.351  -14.461   -5.695  1.00  0.00     1    PROT        13

julia> atoms[1] # デフォルトの表示メソッド
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
      13    N     CYS     A        2        2   -6.351  -14.461   -5.695  1.00  0.00     1    PROT        13
```
