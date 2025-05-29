```julia
mutable struct TestFunctionFactory
```

境界フラックス計算のためのテスト関数を計算するために使用されるDenseSystemを含むデータ構造。

  * `system::VoronoiFVM.AbstractSystem`: 元のシステム
  * `tfsystem::VoronoiFVM.System{Tv, Tc, Ti, Tm, Matrix{Ti}, Matrix{Tv}} where {Tv, Tc, Ti, Tm}`: テスト関数システム
  * `control::VoronoiFVM.SolverControl`: ソルバー制御
