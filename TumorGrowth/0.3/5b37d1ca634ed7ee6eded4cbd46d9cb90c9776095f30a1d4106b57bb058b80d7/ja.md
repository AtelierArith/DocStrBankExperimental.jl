```
solve!(problem, n)
```

キャリブレーション `problem` を解決します。これは [`CalibrationProblem`](@ref) を使用して構築されます。キャリブレーションされたパラメータは `solution(problem)` によって返されます。

ガウス-ニュートン最適化手法（`LevenbergMarquardt` または `Dogleg`）を使用する場合は、`n=0` を指定して `n` を自動的に選択します。

---

```
solve!(problem, controls...)
```

イテレーション `controls` を1つ以上使用してキャリブレーション `problem` を解決します。これは IterationControls.jl パッケージからのものです。例については [`CalibrationProblem`](@ref) の「拡張ヘルプ」セクションを参照してください。

ガウス-ニュートン最適化手法（`LevenbergMarquardt` または `Dogleg`）には推奨されません。
