```julia
(1)
function genDataMatrix(t::Int, n::Int, A=nothing)

(2)
function genDataMatrix(::Type{Complex{T}},
                       t::Int, n::Int, A=○) where {T<:AbstractFloat}
```

(1) $t⋅n$ のランダムデータ行列 $XA$ を生成します。ここで、$X$ はガウス分布からランダムに抽出されたエントリを持つ $t⋅n$ 行列であり、$A$ は $n⋅n$ の対称行列です。引数 `A` として提供されない場合、$A$ は一様分布 ∈[-1, 1] からランダムに抽出されたエントリを持つように生成されます。

(2) (1) と同様ですが、$X$ は複素ガウス分布からランダムに生成され、$A$ はエルミート（複素）であり、引数 `A` として提供されない場合、$A$ は一様分布 ∈[-1-i1, 1+i1] からランダムに抽出されたエントリを持つように生成されます。

**例:**

```julia
A=genDataMatrix(100, 20) # (1)、実数
A=genDataMatrix(ComplexF64, 100, 20) # (2)、複素数
```
