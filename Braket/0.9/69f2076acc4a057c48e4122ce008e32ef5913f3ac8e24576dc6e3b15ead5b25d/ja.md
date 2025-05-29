```
Circuit(v)
```

`Vector`のような`v`から`Circuit`を構築します。`v`には以下のタプルが含まれます：

  * [`Gate`](@ref)、[`Noise`](@ref)、または[`Result`](@ref)
  * 演算子を適用するターゲットキュービット
  * 演算子への任意の構築引数、例えば角度や[`Observable`](@ref Braket.Observables.Observable)

# 例

```jldoctest
julia> v = [(H, collect(0:10)), (Rx, 1, 0.2), (BitFlip, 0, 0.1)];

julia> Circuit(v);
```
