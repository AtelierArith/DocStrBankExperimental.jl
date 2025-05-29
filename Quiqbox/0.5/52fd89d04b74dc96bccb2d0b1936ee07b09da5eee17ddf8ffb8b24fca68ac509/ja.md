```
GDconfig{T, M, ST<:Union{Array{T, 0}, T}} <: ConfigBox{T, GDconfig, M}
```

デフォルトの勾配降下法に使用される設定の可変コンテナで、パラメータを最適化します。

≡≡≡ フィールド ≡≡≡

`lineSearchMethod::M`: 各勾配降下の反復におけるステップサイズを最適化するために選択されたラインサーチメソッドです。これは、Juliaパッケージ [LineSearches.jl](https://github.com/JuliaNLSolvers/LineSearches.jl) に定義された任意のアルゴリズム、または [`itself`](@ref) であり、すべての反復中にステップサイズが定数値に固定されます。

`initialStep::ST`: 各反復における初期ステップサイズの値です。もしそれが `Array{T, 0}` であれば、現在の相互作用での最終ステップサイズ（`lineSearchMethod` によって最適化されたもの）が次の反復の初期ステップサイズとして設定されます。

`stepBound::NTuple{2, T}`: ステップサイズの下限と上限を強制するためのもので、`stepBound[begin] ≤ η ≤ stepBound[end]`（ここで `η` は各反復におけるステップサイズ）を満たします。サイズが境界を超えると、境界値にクリップされます。

`scaleStepBound::Bool`: 各反復における勾配降下のノルムが最初に設定された `stepBound` 内に制約されるように `stepBound` がスケーリングされるかどうかを決定します。すなわち、`stepBound[begin] ≤ norm(η*∇f) ≤ stepBound[end]`（ここで `∇f` は各反復における関数 `f` の勾配）です。

≡≡≡ 初期化メソッド ≡≡≡

```
GDconfig(lineSearchMethod::M=BackTracking(), 
         initialStep::Union{Array{T, 0}, T}=ifelse(M==typeof(Quiqbox.itself), 0.1, 1.0); 
         stepBound::NTuple{2, T}=convert.(eltype(initialStep), (0, Inf)), 
         scaleStepBound::Bool=ifelse(M==typeof(itself), true, false)) where 
        {M, T<:AbstractFloat} -> 
GDconfig{T, M, typeof(initialStep)}
```
