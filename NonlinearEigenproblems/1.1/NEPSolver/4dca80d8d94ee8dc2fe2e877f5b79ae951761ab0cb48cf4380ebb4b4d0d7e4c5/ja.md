```
struct IARInnerSolver
function IARInnerSolver(;tol=1e-13,maxit=80,
           starting_vector=:ones,normalize_DEPs=:auto,
           iar_function=iar)
```

[`iar`](@ref)、[`tiar`](@ref) または [`iar_chebyshev`](@ref) を使用して、`tol` と `maxit` で指定された許容誤差と最大反復回数を持つ内部問題を解決します。開始ベクトルは `:ones` または `:randn` であることができます。`iar_function` は `iar`、`tiar` または `iar_chebyshev`（または同じパラメータを入力として受け取る任意の関数）であることができます。`normalize_DEPs` は、事前計算を実行し、[`DEP`](@ref) の射影が再び `DEP` であることを確認する必要があるかどうかを決定します（これによりパフォーマンスが向上する可能性があります）。値は `true`、`false` または `:auto` を取ることができます。`:auto` は、`iar_chebyshev` ソルバーを使用する場合に `true` に設定されます。

キーワード引数 `iar_function` は、呼び出される `Function` を指定します。関数の例には `iar` と `iar_chebyshev` があります。これらのメソッドと同じキーワード引数を受け取る任意の NEP ソルバーであることができます。

参照: [`InnerSolver`](@ref)、[`inner_solve`](@ref)
