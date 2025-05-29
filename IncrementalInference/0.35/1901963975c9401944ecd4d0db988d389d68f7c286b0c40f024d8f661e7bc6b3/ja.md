```julia
approxConvBelief(dfg, from, target; ...)
approxConvBelief(
    dfg,
    from,
    target,
    measurement;
    solveKey,
    N,
    tfg,
    setPPEmethod,
    setPPE,
    path,
    skipSolve,
    nullSurplus
)

```

`fctLabels` にリストされた順序で畳み込みの逐次系列を計算し、最初の変数に既に含まれている値から開始します。  

ノート

  * `target` は変数でなければなりません。
  * 最終的な `target` 変数は、n-ary因子を通じてパスを発見するために与えられなければなりません。
  * `fctLabels` の最初の要素が単一の `<:AbstractPrior` の場合、新しい出発点が使用されます。
  * この関数は `dfg` の値を変更せず、この要件を満たすためにわずかに速度性能が低下する可能性があります。
  * `tfg` を渡すことで、連鎖内のすべての畳み込みの回復可能な結果を得ることができます。
  * `setPPE` と `setPPEmethod` は、一時的な `tfg` にPPE情報を保存するために使用できます。

開発ノート

  * TODO この関数は単一の因子/変数のケースで非常に効率的である必要があります！
  * FIXME `accumulateFactorMeans` と統合する必要があります
  * TODO `solveKey` はまだすべての場所で完全に接続されていません

      * tfg はソース `dfg` 変数内のすべての solveKeys を取得します
  * TODO PPEオプションに対する approxConv を追加

      * [`accumulateFactorMeans`](@ref)、`approxConvBinary` と統合します

関連

[`approxDeconv`](@ref)、`findShortestPathDijkstra`
