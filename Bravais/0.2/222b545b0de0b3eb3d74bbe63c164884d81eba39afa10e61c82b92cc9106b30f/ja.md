```
dualbasis(Vs)
```

基底 `Vs` の双対基底（時には逆基底とも呼ばれる）を `D` 次元で返します。

入力基底 `Vs` は次のように提供できます：

  * `D` 次元の `StaticVector` の `AbstractVector` の、
  * `D` 次元の `NTuple` の `AbstractVector` の、
  * または、型不安定に、任意の `AbstractVector` の反復可能なものとして。

`Vs` が [`DirectBasis`](@ref) の場合、返される双対格子の型は [`ReciprocalBasis`](@ref) であり、その逆もまた然りです。他の入力タイプの場合、返される型は `SVector{D, <:SVector{D}}` です。
