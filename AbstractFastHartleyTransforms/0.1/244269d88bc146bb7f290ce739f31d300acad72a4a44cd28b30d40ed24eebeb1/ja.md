```
plan_fht(A [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

与えられた次元（`dims`）の配列の形状と型に一致する最適化されたFHTを事前に計画します。（最初の2つの引数は[`fht`](@ref)と同じ意味を持ちます。）FHTによって計算された線形演算子を表すオブジェクト`P`を返し、`fht(A, dims)`を迅速に計算するために必要なすべての情報を含みます。
