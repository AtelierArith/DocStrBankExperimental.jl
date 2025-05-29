```
Declarative(;memory=, filtered=(:isa,:retrieved))
```

宣言的メモリモジュール

# フィールド

  * `memory=Chunk[]`: チャンクの配列
  * `filtered`: 部分一致がオンのときでも正確に一致しなければならないスロット。デフォルトでは、`filtered=(:isa,:retrieved)`
  * `buffer`: 1つのチャンクを含む配列
  * `state`: バッファの状態
