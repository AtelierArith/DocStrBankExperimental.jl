```julia
function barycenter(metric :: Metric, 𝐏:: ℍVector;
              w        :: Vector = [],
              ✓w       :: Bool    = true,
              meanInit :: Union{ℍ, Nothing} = nothing,
              tol      :: Real   = 0.,
              ⏩      :: Bool    = true)
```

通常、この関数は[`fit`](@ref)関数によって呼び出されるため、必要ありません。

`metric`の型が[Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1)であること、エルミート行列の[ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1)である$𝐏$、およびオプションの非負実数重みベクトル`w`を与えると、$𝐏$内の行列の（重み付き）平均を返します。これはMDMモデルのフィッティングに使用されます。

この関数は、選択された`metric`に応じて、[PostDefManifold](https://marco-congedo.github.io/PosDefManifold.jl/dev/)パッケージの適切な平均関数を呼び出し、平均が反復アルゴリズムによって見つけられた場合、反復アルゴリズムが収束することを確認します。

オプションのキーワード引数`w`、`✓w`、`meanInit`、`tol`、および`⏩`の意味については、[mean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Statistics.mean)関数のメソッド(3)を参照してください。

返される平均は、Juliaによってエルミート行列としてフラグ付けされます（[LinearAlgebra](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/)を参照）。
