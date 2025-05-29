```julia
getCliqDownMsgsAfterDownSolve(
    subdfg,
    cliq,
    solveKey;
    status,
    sender
)

```

このクリークのすべての前面およびセパレータ信念から構成されるダウンメッセージの辞書を返します。

ノート：

  * `cliq` に従って `subdfg` から数値結果を取得します。
  * LikelihoodMessage を返します。
