```
POVM( Π :: Vector{POVMel{T}} ) <: Measurement{T}
POVM( Π :: Vector{Matrix{T}} ) <: Measurement{T}
```

正の演算子値測定（POVM）は、一般的な量子測定を表します。各POVM要素はエルミートで、正定値の行列です。すべてのPOVM要素の合計は単位行列を生成します。コンストラクタ `POVM(Π)` は、提供された行列の配列 `Π` が有効なPOVMでない場合に `DomainError` をスローします。
