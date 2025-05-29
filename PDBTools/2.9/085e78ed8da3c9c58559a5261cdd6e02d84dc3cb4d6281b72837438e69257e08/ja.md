```
add_hydrogens!(atoms::AbstractVector{<:Atom}; pH=7.0, obabel="obabel", debug=false)
```

Open Babelを使用してPDBファイルに水素を追加します。

# 引数

  * `atoms::AbstractVector{<:Atom}`: 水素を追加する構造（通常はタンパク質のPDBファイル）。
  * `pH`: 溶液のpH。デフォルトは7.0。
  * `obabel`: obabel実行可能ファイルへのパス。デフォルトは"obabel"。
  * `debug`: trueの場合、obabelからの出力メッセージを表示します。デフォルトはfalse。

!!! note
    この関数は[OpenBabel](http://openbabel.org/)のインストールを必要とします。使用する場合は、対応する参考文献を引用してください。


# 例

```julia-repl
julia> using PDBTools

julia> atoms = read_pdb(PDBTools.TESTPDB, "protein and not element H");

julia> add_hydrogens!(atoms)
   Vector{Atom{Nothing}} with 1459 atoms with fields:
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
       1    N     ALA     A        1        1   -9.229  -14.861   -5.481  1.00  0.00     1       -         1
       2   CA     ALA     A        1        1   -8.483  -14.912   -6.726  1.00  0.00     1       -         2
       3   CB     ALA     A        1        1   -9.383  -14.465   -7.880  1.00  0.00     1       -         3
                                                       ⋮ 
    1457    H     THR     A      104      208    5.886  -10.722   -7.797  1.00  0.00     1       -      1457
    1458    H     THR     A      104      208    5.871  -10.612   -9.541  1.00  0.00     1       -      1458
    1459    H     THR     A      104      208    6.423  -12.076   -8.762  1.00  0.00     1       -      1459
```
