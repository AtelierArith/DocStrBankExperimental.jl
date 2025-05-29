```julia
function predict(model :: SVMmodel,
			𝐏Te	:: Union{ℍVector, Matrix{Float64}},
			what	:: Symbol = :labels;
		meanISR	:: Union{ℍ, Nothing, UniformScaling} = nothing,
		pipeline:: Union{Pipeline, Nothing} = nothing,
		verbose	:: Bool = true,
		⏩	:: Bool = true)
```

2クラスで訓練（フィッティング）された[`SVM`](@ref) `model`と、タイプ[ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1)の*k*個の正定値行列からなるテストセット`𝐏Te`を与えて予測を計算します。

引数`what`、`meanISR`、`pipeline`、および`verbose`の意味については、ENLRモデルの[`predict`](@ref)関数のドキュメントを参照してください。

⏩がtrue（デフォルト）で、`𝐏Te`がℍVectorタイプの場合、接空間への射影はマルチスレッドで行われます。また、LIBSVM.jlの予測関数の予測もマルチスレッドで行われます。

**参照**: [notation & nomenclature](@ref)、[ℍVectorタイプ](@ref)

**関連**: [`fit`](@ref)、[`crval`](@ref)、[`predictErr`](@ref)

**例** 

ENLRモデルの[`predict`](@ref)関数の例を参照してください。構文は同じですが、そこで使用されるモデルを`SVMmodel`に変更する必要があります。
