```
maximal_subgroups(num::Integer, AG::Type{<:AbstractGroup}=SpaceGrop{3}; kind)
```

指定された数 `num` とタイプ `AG` の群の最大部分群のグラフ構造を `GroupRelationGraph` として返します。

## 可視化

得られた群の構造は、`plot(::GroupRelationGraph)` を使用して Makie.jl (例: GLMakie.jl) でプロットできます：

```jl
julia> using Crystalline
julia> gr = maximal_subgroups(112, SpaceGroup{3})
julia> using GraphMakie, GLMakie
julia> plot(gr)
```

## キーワード引数

  * `kind` (デフォルト, `Crystalline.TRANSLATIONENGLEICHE`): klassengleiche 関係を返すには、`kind = Crystalline.KLASSENGLEICHE` を設定します。klassengleiche 関係については、合理的に低いインデックスの関係の選択のみが返されます。

## データソース

この関数によって返される群の関係は、ビルバオ結晶学サーバーの [MAXSUB](https://www.cryst.ehu.es/cryst/maxsub.html) プログラムから取得されました。MAXSUB に関連する元の参考文献を引用してください：

  * Aroyo et al., [Z. Kristallogr. Cryst. Mater. **221**, 15 (2006)](https://doi.org/10.1524/zkri.2006.221.1.15).

```
