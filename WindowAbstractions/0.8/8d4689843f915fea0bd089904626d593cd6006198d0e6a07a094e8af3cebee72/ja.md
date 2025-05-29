特定のウィンドウで発生する可能性のある入力またはウィンドウイベントの種類。

このタイプはビットマスクとして定義されており、イベントのセットを扱いやすくしています。

```julia
struct EventType <: BitMasks.BitMask{UInt32}
```

  * `val::UInt32`
