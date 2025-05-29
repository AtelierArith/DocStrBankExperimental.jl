```
MeanExitTimeProblem
```

平均退出時間問題を表す問題を定義するための構造体：

$$
\div\left[D(\vb x)\grad T\right] =-1
$$

領域 $\Omega$ 内で。この問題は [`PoissonsEquation`](@ref) の特別なケースですが、十分に一般的であるため、別々に定義されています；`MeanExitTimeProblem` は [`PoissonsEquation`](@ref) を使用して構築されます。

この問題は [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)) を使用して解決できます。

# コンストラクタ

```
MeanExitTimeProblem(mesh::FVMGeometry,
    BCs::BoundaryConditions,
    ICs::InternalConditions=InternalConditions();
    diffusion_function,
    diffusion_parameters=nothing,
    kwargs...)
```

## 引数

  * `mesh::FVMGeometry`: [`FVMGeometry`](@ref)。
  * `BCs::BoundaryConditions`: [`BoundaryConditions`](@ref)。
  * `ICs::InternalConditions=InternalConditions()`: [`InternalConditions`](@ref)。

`BCs` と `ICs` の関数は使用されません。`[Neumann](@ref)` 条件または `[Dirichlet](@ref)` 条件に遭遇した場合、条件は均質であると仮定されます。条件が [`Dudt`](@ref) または [`Constrained`](@ref) タイプのいずれかである場合、エラーがスローされます。

## キーワード引数

  * `diffusion_function`: 拡散関数。形式は `(x, y, p) -> Number` である必要があります。ここで `p` は以下の `diffusion_parameters` です。
  * `diffusion_parameters=nothing`: `diffusion_function` の引数 `p`。
  * `kwargs...`: その他のキーワード引数は、問題を表す `LinearProblem`（LinearSolve.jl から）に渡されます。

# フィールド

この構造体には、上記の引数に加えて追加のフィールドがあります：

  * `A`: これはスパース行列 `A` で、`AT = b` となります。
  * `b`: 上記の `b`。
  * `problem`: 問題を表す `LinearProblem`。これは、構造体に対して [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)) を呼び出すときに解決される問題です。
