```
exec_type2!(vp::AbstractVector{T}, p::PlanNUFFT{T}, ûs::AbstractArray{Z})
exec_type2!(vp::NTuple{N,AbstractVector{T}}, p::PlanNUFFT{T}, ûs::NTuple{N,AbstractArray{Z}})
```

タイプ2のNUFFTを実行します（均一グリッドから非均一点へ）。

ここで`ûs`は均一グリッドの入力係数を含みます。非均一点での変換の結果は`vp`に書き込まれます。

まず、[`set_points!`](@ref)を使用して非均一点を設定する必要があります。

複数の変換を一度に実行するには、`vp`と`ûs`の両方が配列のタプルである必要があります（上記の第二のバリアント）。これは、`ntransforms = Val(N)`で初期化されたプランが必要であることに注意してください（[`PlanNUFFT`](@ref）を参照）。

入力タイプは`Z = complex(T)`を満たす必要があります。これは次のことを意味します：

  * 実データ変換の場合、`Z = Complex{T}`（ここで`T <: Real`）；
  * 複素データ変換の場合、`Z = T`（ここで`T <: Complex`）。

さらに[`exec_type1!`](@ref)も参照してください。
