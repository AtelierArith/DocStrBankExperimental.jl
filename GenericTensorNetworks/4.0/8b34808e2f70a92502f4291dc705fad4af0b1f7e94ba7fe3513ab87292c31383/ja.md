```
GraphPolynomial{METHOD} <: AbstractProperty
GraphPolynomial(; method=:finitefield, kwargs...)
```

グラフ多項式を計算します。例えば、[`IndependentSet`](@ref) 問題の場合、これは独立多項式です。`METHOD` 型パラメータは次のシンボルのいずれかである必要があります。

## メソッド引数

  * `:finitefield`、有限体代数を使用して多項式をフィットさせます。

      * 対応するテンソル要素型は [`Mods.Mod`](@ref) です。
      * 丸め誤差はありません。
      * GPU がサポートされています。
      * キーワード引数 `maxorder`（オプション、例えば [`IndependentSet`](@ref) 問題の MIS サイズ）を受け入れます。
  * `:polynomial` および `:laurent`、(ローレン)多項式数を使用して多項式を直接解決します。

      * 対応するテンソル要素型は [`Polynomial`](https://juliamath.github.io/Polynomials.jl/stable/polynomials/polynomial/#Polynomial-2) および [`LaurentPolynomial`](https://juliamath.github.io/Polynomials.jl/stable/polynomials/polynomial/#Polynomials.LaurentPolynomial) です。
      * カウントを保存するデータ型に応じて、小さな丸め誤差がある可能性があります。
      * グラフサイズに対して線形のメモリオーバーヘッドがあります。
  * `:fft`、高速フーリエ変換を使用して多項式をフィットさせます。

      * 対応するテンソル要素型は `Base.Complex` です。
      * （制御可能な）丸め誤差があります。
      * BLAS および GPU がサポートされています。
      * キーワード引数 `maxorder`（オプション）および `r` を受け入れます。`r > 1` の場合、大きな次数の係数の精度が向上し、`r < 1` の場合、小さな次数の係数の精度が向上します。
  * `:fitting`、多項式を直接フィットさせます。

      * 対応するテンソル要素型は `Base.Float64` のような浮動小数点数です。
      * 丸め誤差があります。
      * BLAS および GPU がサポートされており、すべてのメソッドの中で最も高速です。

グラフ多項式は、重み付き制約充足問題には定義されていません。
