```
AbstractLinearMap{T, TS}
```

要素タイプ `T` とサイズ `TS` を持つ一般的な線形写像を表します。

## 概要

**線形写像** は、次の条件を満たす変換 `L` です：

  * **加法性**:    `math   L(u + v) = L(u) + L(v)`
  * **同次性**:    `math   L(cu) = cL(u)`

通常、これは `size` で与えられる次元を持つ行列として表され、この抽象型は行列が明示的に利用できない場合にこの写像を定義するのに役立ちます。

## メソッド

  * `Base.eltype(A)`: 要素タイプ `T` を返します。
  * `Base.size(A)`: サイズ `A.size` を返します。
  * `Base.size(A, i)`: `i` 番目の次元を返します。

## 例

例として、Arnoldi-Lindblad 固有値ソルバーの [`eigsolve_al`](@ref) 関数で使用される線形写像を定義します：

```julia
struct ArnoldiLindbladIntegratorMap{T,TS,TI} <: AbstractLinearMap{T,TS}
    elty::Type{T}
    size::TS
    integrator::TI
end

function LinearAlgebra.mul!(y::AbstractVector, A::ArnoldiLindbladIntegratorMap, x::AbstractVector)
    reinit!(A.integrator, x)
    solve!(A.integrator)
    return copyto!(y, A.integrator.u)
end
```

ここで `integrator` は時間発展のための ODE インテグレーターです。このようにして、[`eigsolve`](@ref) 関数を使用してこの線形写像を対角化することができます。
