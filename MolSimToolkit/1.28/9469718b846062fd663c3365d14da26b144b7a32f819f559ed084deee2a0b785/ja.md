```
ss_heatmap(ssmap::Matrix{<:Real}; scalex=1.0, kargs...)
```

二次構造マップのヒートマップをプロットします。

!!! note
    この関数は `Plots` パッケージの読み込みを必要とします。`residue_ticks` 関数は `PDBTools` パッケージで利用可能です。


`scalex` キーワード引数は、通常シミュレーションにおける時間を意味する x 軸をスケーリングするために使用できます。デフォルトでは 1.0 で、x 軸はフレーム番号です。

`kargs` キーワード引数は、プロットのプロパティを変更するために Plots パッケージの `heatmap` 関数に渡されます。特に：

  * 残基の目盛りは `yticks` で設定でき、`PDBTools` の `residue_ticks` 関数を使用して残基特有のラベルに設定できます。
  * x 軸のラベルは `xlabel` で適切な単位（例えば "time / ns"）に設定でき、`scalex` と組み合わせて使用します。

## 例

```julia-repl
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> using Plots, PDBTools

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> ssmap = ss_map(simulation; ss_method=stride_run, show_progress=false);

julia> protein = select(atoms(simulation), "protein");

julia> ss_heatmap(ssmap; scalex=0.1, xlabel="time / ns", yticks=residue_ticks(prot; stride=5))
```

二次構造マップのヒートマップがプロットされ、x 軸は 0.1 にスケーリングされ、残基の目盛りは 5 残基ごとに設定されます。プロットは Plots パッケージの `savefig` 関数を使用して保存できます。
