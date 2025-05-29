```
exec_type1!(ûs::AbstractArray{Z}, p::PlanNUFFT{T}, vp::AbstractVector{T})
exec_type1!(ûs::NTuple{N,AbstractArray{Z}}, p::PlanNUFFT{T}, vp::NTuple{N,AbstractVector{T}})
```

タイプ1のNUFFTを実行します（非均一な点から均一なグリッドへ）。

ここで`vp`は非均一な点での入力値を含みます。変換の結果は`ûs`に書き込まれます。

最初に[`set_points!`](@ref)を使用して非均一な点を設定する必要があります。

複数の変換を一度に実行するには、`vp`と`ûs`の両方が配列のタプルである必要があります（上記の第二のバリアント）。これは、`ntransforms = Val(N)`で初期化されたプランが必要であることに注意してください（[`PlanNUFFT`](@ref）を参照）。

入力タイプは`Z = complex(T)`を満たす必要があります。これは次のことを意味します：

  * 実データ変換の場合、`Z = Complex{T}`（ここで`T <: Real`）；
  * 複素データ変換の場合、`Z = T`（ここで`T <: Complex`）。

さらに[`exec_type2!`](@ref)も参照してください。
