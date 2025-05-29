```
MetopDiskArray{T, N} <: AbstractMetopDiskArray{T, N}
```

Metop製品内の変数の遅延読み込みを処理するための構造体。製品内の生の型は、スケーリングなしでマッピングされます。`RecordSubType`の自動変換を有効にすることができます。例えば、`VInteger`を`Float64`に変換することができます。
