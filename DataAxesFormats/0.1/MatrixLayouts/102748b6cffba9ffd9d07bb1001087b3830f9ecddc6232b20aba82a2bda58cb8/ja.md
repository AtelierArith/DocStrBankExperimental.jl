```
relayout!(destination::AbstractMatrix, source::AbstractMatrix)::AbstractMatrix
relayout!(destination::AbstractMatrix, source::NamedMatrix)::NamedMatrix
```

同じ `matrix` データを返しますが、他のメモリレイアウトで。

列優先のUMI行列があり、その行が細胞で、列が遺伝子であると仮定します。したがって、遺伝子のUMIを合計するのは速いですが、細胞のUMIを合計するのは遅くなります。行列の `transpose`（`!`なし）は速いです。これは、軸が反転した行列のゼロコピーラッパーを作成するため、行は遺伝子、列は細胞になりますが、行優先レイアウトになります。したがって、**依然として**、遺伝子のUMIを合計するのは速く、細胞のUMIを合計するのは遅いです。

対照的に、`transpose!`（`!`あり）（または [`transposer`](@ref)）は遅いです。これは、データの再配置されたコピーを作成し、行は遺伝子、列は細胞の行列を返しますが、今度は列優先レイアウトになります。したがって、この場合、遺伝子のUMIを合計するのは遅く、細胞のUMIを合計するのは速くなります。

!!! note
    行列を `relayout!` してからデータの「穀物に沿った」操作を行うことは、ほぼ常に価値があります。これをスキップしてデータの「穀物に逆らった」操作を行うのは避けるべきです。これは（少なくともJuliaでは）`transpose!` の実装がそのタスクに最適化されているのに対し、他の操作は通常、データの「穀物に逆らった」作業に特定の最適化を提供しないためです。`relayout!` の利点は、一連の操作を行う際にさらに重要になります（例：各細胞の遺伝子UMIを合計し、これらの合計から遺伝子UMIを分数に変換し、その分数の対数を計算する）。


`transpose`（`!`なし）で `transpose!`（`!`あり）の結果を転置すると、元の行列と**見た目**は同じ（行は細胞、列は遺伝子）ですが、**動作**は**異なります** - 遺伝子のUMIを合計するのは遅く、細胞のUMIを合計するのは速いです。この `transpose` の `transpose!` は一般的なイディオムであり、基本的に `relayout!` があなたのために行うことです。さらに、`relayout!` は疎行列と密行列の両方で機能し、`destination` が指定されていない場合は、自動的に `similar` 行列が割り当てられます。

!!! note
    呼び出し元は、適切な `destination` 行列（疎行列には疎、非疎行列には密）を提供する責任があります。これは転置行列である可能性があります。`source` が `NamedMatrix` の場合、結果は同じ軸を持つ `NamedMatrix` になります。`destination` も `NamedMatrix` の場合、その軸は `source` と一致しなければなりません。


```
