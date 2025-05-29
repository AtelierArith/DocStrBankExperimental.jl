```julia
printHistoryLane(fid, linecounter, hiVec)
printHistoryLane(fid, linecounter, hiVec, seqLookup)

```

すべてのクリーク状態遷移機械の履歴を要約した1行のレーンを印刷します。

ノート

  * hiVecは、`fid`に1行として印刷するすべてのクリーク（すなわちレーン）のベクトルです。

      * グローバルカウンター（デフォルトのCSMカウンターではない）を持つ`::Tuple{Int,..}`を含みます。
  * `CSMHistoryTuple`のベクトル

関連:

printCliqHistoryLogical, printCliqHistoryLine
