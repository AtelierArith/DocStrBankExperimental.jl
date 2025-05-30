```julia
nodeflux(system, U)

```

三角形分割のノード上でのベクトル関数としてのエッジフラックスの再構成。結果は、フラックス密度を示す離散化ノードによって張られたFEM空間における区分線形ベクトル関数として見ることができます。

再構成は、"魔法の公式" R. Eymard, T. Gallouet, R. Herbin, IMA Journal of Numerical Analysis (2006) 26, 326−353, Lemma 2.4 に基づいています。

戻り値は `dim x nspec x nnodes` のベクトルです。種 i のフラックスは、例えば GridVisualize.vectorplot を介してプロットできます。

例:

```julia
    ispec=3
    vis=GridVisualizer(Plotter=Plotter)
    scalarplot!(vis,grid,solution[ispec,:],clear=true,colormap=:summer)
    vectorplot!(vis,grid,nf[:,ispec,:],clear=false)
    reveal(vis)
```

注意: コード内のドメインコーナーの値に関して未解決の問題がある可能性があります。この問題の現れとして、潜在的な境界アーティファクトを確認し、報告してください。
