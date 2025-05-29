```
struct NewtonInnerSolver
function NewtonInnerSolver(;tol=1e-13,maxit=80,starting_vector=:Vk,
                           newton_function=augnewton)
```

内部問題を解決するためにニュートン類似の方法を使用し、許容誤差と最大反復回数はそれぞれ `tol` と `maxit` で指定されます。開始ベクトルは `:ones`、 `:randn`、または `:Vk` にすることができます。値 `:Vk` は外部 NEPソルバーのキーワード引数（`Vk`）の使用を指定します。これは通常、外部メソッドでの前の反復値です。

キーワード引数 `newton_function` は呼び出される `Function` を指定します。この型は [`augnewton`](@ref)、[`newton`](@ref)、[`resinv`](@ref)、[`quasinewton`](@ref)、[`newtonqr`](@ref) をサポートしています。原則として、これらのメソッドと同じキーワード引数を取る任意のメソッドを使用できます。

関連情報: [`InnerSolver`](@ref)、[`inner_solve`](@ref)
