```
SetGridRule <: Rule
```

`Rule` は全体のグリッドに適用されます。これは、近隣のバッファリングやグリッドのループ処理が必要ない操作や、特定の最適化が必要ない操作に使用されます。`rand!(grid)` のような単純な関数や、DSP.jlのような他のパッケージからの畳み込みを使用するのに最適です。また、シミュレーション中にDynamicGrids.jlフレームワークに収まらない他のカスタムなことを行うのにも役立つかもしれません。

グリッドルールは、必要なグリッドを指定し、他のグリッドと同様にシーケンスされます。

```julia
struct MySetGridRule{R,W} <: SetGridRule{R,W} end
```

そして、次のように適用されます：

```julia
function applyrule!(data::AbstractSimData, rule::MySetGridRule{R,W}) where {R,W}
    rand!(data[W])
end
```
