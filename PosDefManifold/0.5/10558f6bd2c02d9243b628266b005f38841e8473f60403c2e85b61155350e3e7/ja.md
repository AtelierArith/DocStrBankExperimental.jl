trade(P::ℍ{T}) where T<:RealOrComplex

正定値行列 `P` を与えると、`P` の *トレース* と *行列式* を 2 タプルとして返します。これは、2 次元で正の行列をプロットするために使用されます (*TraDe プロット*: log(trace/n) 対 log(determinant)、以下の例を参照してください)。

`P` はジュリアによって `Hermitian` としてフラグ付けされる必要があります。 [行列の型キャスティング](@ref)を参照してください。

**例**

```julia
using PosDefManifold
P=randP(3)
t, d=trade(P)  # (t, d)=trade(P) と同等

# TraDe プロット
using Plots
k=100
n=10
𝐏=randP(n, k, SNR=1000); # 100 個の実 Hermitian 行列
x=Vector{Float64}(undef, k)
y=Vector{Float64}(undef, k)
for i=1:k
    x[i], y[i] = trade(𝐏[i])
end
x=log.(x./n)
y=log.(y)
plot(x, y, seriestype=:scatter)
```
