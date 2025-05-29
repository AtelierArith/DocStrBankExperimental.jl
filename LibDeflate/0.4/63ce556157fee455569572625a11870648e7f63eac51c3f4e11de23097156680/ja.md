```
crc32(data, start=UInt32(0))::UInt32
```

`data`のcrc32チェックサムを計算し、シード`start`（デフォルトは0）を使用します。crc32は、Julia標準ライブラリで提供されている`crc32c`とは異なる、より遅いアルゴリズムであることに注意してください。

参照: [`unsafe_crc32`](@ref)
