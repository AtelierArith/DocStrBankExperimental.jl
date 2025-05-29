```
StencilRecurrencePlan{N, D, S, COEF<:NTuple{S,Function}, INIT<:Function} <: AbstractLinearRecurrencePlan
```

# パラメータ

  * `N`: システム次元
  * `D`: 数値ドメイン、例: `Real`, `Complex` など
  * `S`: ステンシルサイズ

# プロパティ

  * `stencil::SVector{S, CartesianIndex{N}}`: ステンシルの相対インデックス。`(0,0)`を含むことができます（`coef`を参照）。
  * `coef::COEF<:NTuple{S,Function}`: 各相対インデックスに関連付けられた係数。`CartesianIndex(0,0)`に関連付けられたものは、そのエントリに追加される定数を指します。関数は `f(T, I...)` の形式である必要があり、ここで `I` はステンシルのインデックス、`T` は提案された戻り値の型です。係数は少なくとも `T` と同じくらい正確である必要があります。`Irrational`、`Rational`、または `Integer` のような正確な値の型が適しており、もしそれが不可能な場合は `BigFloat` でも構いません。
  * `init::INIT<:Function`: 初期値に使用される関数。関数は `f(I...)` または `f(T, I...)` の形式である必要があり、ここで `I` は配列のサイズ（最後の次元を除く）、`T` は精度型です。前者の場合、`f` は正確な値、すなわち `Integer`、`Rational`、または `Irrational` を返す必要があります。
  * `size::Dims{N}`: 全体の配列のサイズ。
  * `offset::NTuple{N,Int}`: 再帰が始まる最初のインデックス。
