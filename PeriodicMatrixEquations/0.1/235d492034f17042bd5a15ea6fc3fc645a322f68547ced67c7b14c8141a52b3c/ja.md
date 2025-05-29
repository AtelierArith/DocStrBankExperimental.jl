```
tvcric_eval(t, W, A, R, Q; adj, solver, reltol, abstol, dt) -> Xval
```

周期リカッティ微分方程式の解の時間値 `Xval := X(t)` を計算します。

```
  .                                                
  X(t) = A(t)X(t) + X(t)A(t)' + Q(t) - X(t)R(t)X(t) ,  X(t0) = W(t0), t0 < t, adj = false (デフォルト) の場合、
```

または 

```
  .                                                
 -X(t) = A(t)'X(t) + X(t)A(t) + Q(t) - X(t)R(t)X(t) ,  X(t0) = W(t0), t0 > t, adj = true の場合、
```

同じ周期行列 `A`、`R`、`Q` とキーワード引数 `adj` の同じ値で、関数 [`pgcric`](@ref) で決定された周期生成器 `W` を使用します。初期時間 `t0` は、`adj = false` の場合は下から、`adj = true` の場合は上から、`t` に最も近い時間グリッド値です。結果として得られる `Xval` は対称行列です。

使用するODEソルバーは、キーワード引数 `solver` を使用して指定できます（デフォルト: `solver = "non-stiff"`）と、必要な相対精度 `reltol`（デフォルト: `reltol = 1.e-4`）および絶対精度 `abstol`（デフォルト: `abstol = 1.e-7`）とともに指定します。望ましい相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから以下のソルバーを選択できます：

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "auto"` - デフォルトのソルバーを使用し、剛性問題を自動的に検出します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5()`）。
