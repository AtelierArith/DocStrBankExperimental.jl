```julia
fifoFreeze!(dfg)

```

`fg.fifo` の順序に従って、`fg.qfl` で定義された準固定遅延長よりも古いノードを凍結します。

将来:

  * fifo 以外の異なる凍結戦略を許可する。
