```
MaskedPauliRotation(symbols::Vector{Symbol}, qinds::Vector{Int}, term::PauliStringType)
```

量子ビット `qinds` に作用するパラメータ化されたパウリ回転ゲートで、パウリ文字列 `symbols` を持ちます。`term` は、量子ビットの総数に対して正しい整数型を持つパウリ文字列の整数表現です。これにより、ゲートの適用がより高速になります。`PauliRotation` からの変換については `tomaskedpaulirotation` を参照してください。これは `MaskedPauliRotation` を構築する最も簡単な方法です。
