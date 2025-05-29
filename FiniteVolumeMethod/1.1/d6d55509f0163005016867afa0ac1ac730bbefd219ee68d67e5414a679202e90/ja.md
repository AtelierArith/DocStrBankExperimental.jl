```
DiffusionEquation <: AbstractFVMTemplate
```

拡散方程式を表す問題を定義するための構造体：

$$
\pdv{u}{t} = \div\left[D(\vb x)\grad u\right]
$$

領域 $\Omega$ 内で。

この問題は [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)) を使用して解決できます。

!!! warning
    この問題の解には追加のコンポーネントが加えられます。元の解は `sol[begin:end-1, :]` の中にあり、ここで `sol` は [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)) によって返される解です。


# コンストラクタ

```
DiffusionEquation(mesh::FVMGeometry,
    BCs::BoundaryConditions,
    ICs::InternalConditions=InternalConditions();
    diffusion_function,
    diffusion_parameters=nothing,
    initial_condition,
    initial_time=0.0,
    final_time,
    kwargs...)
```

## 引数

  * `mesh::FVMGeometry`: [`FVMGeometry`](@ref)。
  * `BCs::BoundaryConditions`: [`BoundaryConditions`](@ref)。これらの境界条件では、すべての関数は依然として `(x, y, t, u, p) -> Number` の形である必要がありますが、`t` と `u` の引数は使用されず、`nothing` に置き換えられます。
  * `ICs::InternalConditions=InternalConditions()`: [`InternalConditions`](@ref)。これらの内部条件では、すべての関数は依然として `(x, y, t, u, p) -> Number` の形である必要がありますが、`t` と `u` の引数は使用されず、`nothing` に置き換えられます。

## キーワード引数

  * `diffusion_function`: 拡散関数。`(x, y, p) -> Number` の形である必要があり、ここで `p = diffusion_parameters` です。
  * `diffusion_parameters=nothing`: `diffusion_function` の引数 `p`。
  * `initial_condition`: 初期条件。
  * `initial_time=0.0`: 初期時間。
  * `final_time`: 最終時間。
  * `kwargs...`: その他のキーワード引数は、問題を表す `ODEProblem` (DifferentialEquations.jl から) に渡されます。

# フィールド

この構造体は、上記の引数に加えて追加のフィールドを持っています：

  * `A`: これは疎行列 `A` で、`du/dt = Au + b` となります。
  * `b`: 上記の `b`。
  * `Aop`: システムを表す `MatrixOperator` で、`du/dt = Aop*u` となります（`u` は追加のコンポーネントでパディングされており、`A` は現在 `Aop` 内にあります）。
  * `problem`: 問題を表す `ODEProblem`。これは、構造体に対して [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)) を呼び出すときに解決される問題です。
