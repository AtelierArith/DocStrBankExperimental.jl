```
MixedFlowpipe{N,RT<:AbstractReachSet{N},FT<:AbstractFlowpipe} <: AbstractFlowpipe
```

同じ時間のフローパイプのベクターをラップする型であり、必ずしも時間的に連続しているわけではありません。

### フィールド

  * `Fk`  – フローパイプのベクター
  * `ext` – （オプション、デフォルト：空）拡張用の辞書

### 注意事項

この型は、フローパイプが時間的に連続しているとは仮定していません。
