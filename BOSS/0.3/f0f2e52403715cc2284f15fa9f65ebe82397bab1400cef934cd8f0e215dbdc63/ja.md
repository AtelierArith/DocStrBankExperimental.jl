出力 `y` の品質を測定するフィットネス関数の抽象型。

フィットネスは、将来の評価のための有望なポイントを決定するために `AcquisitionFunction` によって使用されます。

すべてのフィットネス関数は *次のことを実装する必要があります*：

  * (::CustomFitness)(y::AbstractVector{<:Real}) -> fitness::Real

例外は `NoFitness` であり、明確に定義されたフィットネスを持たない問題に使用できます。その場合、`Fitness` に依存しない `AcquisitionFunction` を使用する必要があります。

関連情報: [`NoFitness`](@ref), [`LinFitness`](@ref), [`NonlinFitness`](@ref), [`AcquisitionFunction`](@ref)
