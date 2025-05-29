```
NonlinearSolveBase.RelTerminationMode <: AbstractNonlinearTerminationMode
```

すべての $| \Delta u | \leq reltol \times | u |$ の場合に終了します。.

$$
\Delta u
$$

は非線形ソルバーによって計算された増分を示し、$u$ は解を示します。
