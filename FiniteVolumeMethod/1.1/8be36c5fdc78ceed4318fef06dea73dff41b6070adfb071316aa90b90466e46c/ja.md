```
LaplacesEquation
```

(一般化された) ラプラス方程式を表す問題を定義するための構造体：

$$
\div[D(\vb x)\grad u] = 0
$$

領域 $\Omega$ 内で。詳細は [`PoissonsEquation`](@ref) を参照してください。

この問題は [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)) を使用して解決できます。

# コンストラクタ

```
LaplacesEquation(mesh::FVMGeometry,
    BCs::BoundaryConditions,
    ICs::InternalConditions=InternalConditions();
    diffusion_function=(x,y,p)->1.0,
    diffusion_parameters=nothing,
    kwargs...)
```

## 引数

  * `mesh::FVMGeometry`: [`FVMGeometry`](@ref)。
  * `BCs::BoundaryConditions`: [`BoundaryConditions`](@ref)。これらの境界条件では、すべての関数は依然として `(x, y, t, u, p) -> Number` の形式である必要がありますが、`t` と `u` の引数は使用されず、`nothing` に置き換えられます。
  * `ICs::InternalConditions=InternalConditions()`: [`InternalConditions`](@ref)。これらの内部条件では、すべての関数は依然として `(x, y, t, u, p) -> Number` の形式である必要がありますが、`t` と `u` の引数は使用されず、`nothing` に置き換えられます。

## キーワード引数

  * `diffusion_function=(x,y,p)->1.0`: 拡散関数。`(x, y, p) -> Number` の形式である必要があり、ここで `p = diffusion_parameters` です。
  * `diffusion_parameters=nothing`: `diffusion_function` の引数 `p`。
  * `kwargs...`: その他のキーワード引数は、問題を表す `LinearProblem` (LinearSolve.jl から) に渡されます。

# フィールド

この構造体には、上記の引数に加えて追加のフィールドがあります：

  * `A`: これは疎行列 `A` で、`Au = b` となります。
  * `b`: 上記の `b`。
  * `problem`: 問題を表す `LinearProblem`。これは、構造体に対して [`solve`](@ref solve(::AbstractFVMTemplate, args...; kwargs...)) を呼び出すときに解決される問題です。
