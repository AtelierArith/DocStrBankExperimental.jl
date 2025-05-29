```julia
mutable struct TestFunctionFactory{Tu, Tv}
```

境界フラックス計算のためのテスト関数を計算するために使用されるDenseSystemを含むデータ構造。

型パラメータ：

  * `Tu`: テスト関数の値の型
  * `Tv`: システムのデフォルト値の型

      * `system::VoronoiFVM.AbstractSystem{Tv} where Tv`: 元のシステム
  * `state::VoronoiFVM.SystemState{Tu, Tp, TMatrix, TGenericMatrix, TSolArray} where {Tu, Tp, TMatrix<:AbstractMatrix{Tu}, TGenericMatrix, TSolArray<:AbstractMatrix{Tu}}`: テスト関数システムの状態
  * `control::VoronoiFVM.SolverControl`: ソルバー制御
