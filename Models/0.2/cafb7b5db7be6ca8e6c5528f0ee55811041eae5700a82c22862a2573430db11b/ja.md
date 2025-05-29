fit(::Template, output::AbstractMatrix, input::AbstractMatrix, [weights]) -> Model

[`Template`](@ref)を`output`および`input`データにフィットさせ、訓練された[`Model`](@ref)を返します。慣例として、`weights`は`StatsBase.uweights(Float32, size(outputs, 2))`にデフォルト設定されています。
