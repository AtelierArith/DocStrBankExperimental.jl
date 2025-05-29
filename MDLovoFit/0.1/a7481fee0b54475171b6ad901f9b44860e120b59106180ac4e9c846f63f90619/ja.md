```
mdlovofit(
    atoms::AbstractVector{<:PDBTools.Atom}, # システムの原子（通常は「タンパク質と名前CA」の選択）
    trajectory_file::String, # 軌道ファイルの名前 
    fraction; # 整列する原子の割合
    output_pdb=nothing, # 出力ファイルの名前。nothingの場合、出力ファイルは書き込まれません
    atoms_to_consider=atoms, # 異なる原子のセットである可能性があります
    first=1, 
    last=nothing, # nothingは軌道の最後のフレームを意味します
    iref=1, # 参照フレーム
    maxframes=100, # 整列するフレームの数
)
```

軌道に対してMDLovoFitを実行します。
