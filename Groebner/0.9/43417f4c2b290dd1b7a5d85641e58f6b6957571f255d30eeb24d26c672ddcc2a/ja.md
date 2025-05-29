```
groebner_apply!(trace, polynomials; options...)
groebner_apply!(trace, batch::NTuple{N, Vector}; options...)
```

与えられた `trace` に従って `polynomials` によって生成されたイデアルのグレブナー基底を計算します。

他にも `groebner_learn` を参照してください。

## 引数

  * `trace`: `groebner_learn` によって生成されたトレース。
  * `polynomials`: 多項式の配列。`GF(p)` または `Nemo.GF(p)` 上の AbstractAlgebra.jl または Nemo.jl の多項式でなければなりません。`N` 個の多項式の配列のタプルを供給して、同時に `N` 個のグレブナー基底を計算することも可能です。これにより、別々に計算するよりも全体的に効率的になる可能性があります。

## 戻り値

タプル (`success`, `basis`) を返します。

  * `success`: 呼び出しが成功したかどうかを示す bool。
  * `basis`: 多項式の配列、グレブナー基底。

## 可能なオプション

`groebner_apply!` 関数は、与えられた `trace` からほとんどのパラメータを自動的に継承します。

## 例

例については、`groebner_learn` のドキュメントを参照してください。

## 注意事項

  * 一般に、`success` は偽陽性である可能性があります。偽陽性の確率は、いくつかの実用的なアプリケーションでは十分に低いと考えられています。
  * この関数は `trace` を変更するため、**スレッドセーフ**ではありません。
  * この関数はプログラムの中断に対して**安全**ではありません。たとえば、`groebner_apply!(trace, ...)` が実行中に `Ctrl + C` を押すと、`trace` が破損する可能性があります。
