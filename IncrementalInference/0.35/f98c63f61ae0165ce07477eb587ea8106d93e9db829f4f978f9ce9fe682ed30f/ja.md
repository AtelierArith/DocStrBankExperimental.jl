```julia
buildCliqSubgraph!(
    cliqSubFg,
    dfg,
    frontals,
    separators;
    solvable,
    verbose,
    solveKey
)

```

クリークのための専門的なサブグラフ関数で、フロンタルとセパレーターのリストを考慮してDFGから深いサブグラフコピーを構築します。開発メモ：

  * TODO クリークはすでにフロンタル、セパレーター、およびポテンシャル（ファクター）のリストを持っているべきなので、この関数はcopyGraphまたはbuildSubgraphの軽いラッパーであるべきです。
  * TODO クリークを送信し、その後フロンタル、セパレーター、およびファクターを抽出します。
  * TODO コピーするsolveKeysを制限する機能。
