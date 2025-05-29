```
nmprt(R[; lmin=2, theiler])
```

最も確率の高い再発時間（NMPRT）を計算し、`lmin`（デフォルトは2）より短い行と、すべての点をTheilerウィンドウ内から除外します（キーワード引数`theiler`のデフォルト値と使用法については[`rqa`](@ref)を参照してください）。

この数値は、システムが最も頻繁に現れる再発時間を使用して再発した回数を示します。つまり、再発時間のヒストグラムの最大値です[1]。

## 参考文献

[1] : E.J. Ngamga *et al.* "Recurrence analysis of strange nonchaotic dynamics", *Physical Review E*, 75(3), 036222(1-8) (2007) [DOI:10.1103/physreve.75.036222](https://doi.org/10.1103/physreve.75.036222)
