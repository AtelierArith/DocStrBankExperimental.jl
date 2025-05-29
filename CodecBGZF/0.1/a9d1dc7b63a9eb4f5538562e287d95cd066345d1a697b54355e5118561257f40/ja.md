```
VirtualOffset(stream::BGZFDecompressorStream)
```

`stream`の現在の位置の`VirtualOffset`を取得します。`stream`の入力ストリームがシーク可能な場合、このオフセットにシークすると、ストリームは現在の状態と同等の状態になります。`BGZFDecompressorStream`は、16の前のブロックのオフセットのみを追跡します。`stream`の出力バッファに16ブロック以上が格納されている場合、この操作は失敗します。
