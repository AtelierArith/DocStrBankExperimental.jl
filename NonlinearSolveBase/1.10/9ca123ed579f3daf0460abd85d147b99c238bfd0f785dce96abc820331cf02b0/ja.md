```
NonlinearSolveBase.AbsNormTerminationMode <: AbstractNonlinearTerminationMode
```

$$
\| \Delta u \| \leq abstol
$$

の場合に終了します。.

$$
\Delta u
$$

は内部非線形ソルバーによって計算された増分を示します。

## コンストラクタ

```
NonlinearSolveBase.AbsNormTerminationMode(internalnorm = nothing)
```

ここで `internalnorm` は終了条件に使用するノルムです。`norm(_, 2)`、`norm`、`norm(_, Inf)`、および `maximum(abs, _)` に対して特別な処理が行われます。.
