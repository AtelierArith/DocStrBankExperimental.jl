```julia
struct DefaultEig{T} <: BifurcationKit.AbstractDirectEigenSolver
```

構造体 `DefaultEig` は `BifurcationKit` に `eigen` メソッドを提供するために使用されます。

## フィールド

  * `which::Any`: 計算された固有値をどのようにソートするか。デフォルト: 実数

## コンストラクタ

上記のフィールドをそのまま渡します。例: `DefaultEig(; which = abs)`
