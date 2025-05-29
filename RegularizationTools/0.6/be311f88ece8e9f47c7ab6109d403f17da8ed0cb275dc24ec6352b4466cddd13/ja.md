```
RegularizationProblem
```

このデータ型は、逆行列計算に使用されるキャッシュされた行列を含んでいます。問題は、設計行列 A とティヒノフ行列 L を入力として、コンストラクタ [setupRegularizationProblem](@ref) を使用して初期化されます。ハット量、例えば Ā は標準形の設計行列として計算されます。ĀĀ、Āᵀ、F̄ は、異なるデータでの繰り返し逆行列計算を高速化するために事前に計算されています。L⁺ₐ は、データを [to*standard*form](@ref) および [to*general*form](@ref) に繰り返し変換するための高速化のためにキャッシュされています。

```
Ā::Matrix{Float64}     # 設計行列の標準形
A::Matrix{Float64}     # 設計行列の一般形 (n×p)
L::Matrix{Float64}     # スムージング行列 (n×p)
ĀĀ::Matrix{Float64}    # パフォーマンスのためにキャッシュされた Ā'Ā の値
Āᵀ::Matrix{Float64}    # パフォーマンスのためにキャッシュされた Ā' の値
F̄::SVD                 # Ā のキャッシュされた SVD 分解
Iₙ::Matrix{Float64}    # キャッシュされた単位行列 n×n
Iₚ::Matrix{Float64}    # キャッシュされた単位行列 p×p
K₀T⁻¹H₀ᵀ::Matrix{Float64} # Hansen ch 2 の 2.42 および 2.44 を計算するためのキャッシュされた値
```
