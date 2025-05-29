```
struct ArnoldiIterator{F,T,O<:Orthogonalizer} <: KrylovIterator{F,T}
ArnoldiIterator(f, v₀, [orth::Orthogonalizer = KrylovDefaults.orth])
```

一般的な線形写像 `f::F` と初期ベクトル `v₀::T` を受け取り、それに基づいて拡張する `ArnoldiFactorization` を生成するイテレータです。特に、`ArnoldiIterator` は、[Arnoldi反復](https://en.wikipedia.org/wiki/Arnoldi_iteration)を使用して、徐々に拡張されるArnoldi因子分解を反復します。

引数 `f` は行列であるか、単一の引数 `v` を受け取る関数であり、`f(v)` がベクトル `v` に対する線形写像の作用を実装します。

オプションの引数 `orth` は、使用する [`Orthogonalizer`](@ref) を指定します。[`KrylovDefaults`](@ref) のデフォルト値は、再直交化ステップを使用する可能性のある [`ModifiedGramSchmidtIR`](@ref) を使用します。

`ArnoldiIterator` のインスタンスを反復する際に生成される値は、[`ArnoldiFactorization`](@ref) のインスタンスであり、例えば次のように [`basis`](@ref)、[`rayleighquotient`](@ref)、[`residual`](@ref)、[`normres`](@ref)、および [`rayleighextension`](@ref) に即座に分解できます。

```julia
for (V, B, r, nr, b) in ArnoldiIterator(f, v₀)
    # 何かをする
    nr < tol && break # 一般的な停止基準
end
```

イテレータは、型 `T` のオブジェクトの基礎となるベクトル空間の次元を知らないため、残差ノルム `nr` が機械精度 `eps(typeof(nr))` を下回るまでKrylov部分空間を拡張し続けます。

`ArnoldiIterator` の内部状態は、返り値と同じであり、すなわち対応する `ArnoldiFactorization` です。しかし、JuliaのBaseイテレーションインターフェース（`Base.iterate`を使用）では状態が変更されないことが要求されるため、次のイテレーションステップごとに `deepcopy` が生成されます。

代わりに、次のインターフェースを使用して、`ArnoldiFactorization` をその場で変更することもできます。例えば、上記の同じ例に対して

```julia
iterator = ArnoldiIterator(f, v₀)
factorization = initialize(iterator)
while normres(factorization) > tol
    expand!(iterator, factorization)
    V, B, r, nr, b = factorization
    # 何かをする
end
```

ここで、[`initialize(::KrylovIterator)`](@ref) は長さ1の最初のKrylov因子分解を生成し、`expand!(::KrylovIterator, ::KrylovFactorization)`(@ref) は因子分解をその場で拡張します。また、既存の因子分解を初期化するための [`initialize!(::KrylovIterator, ::KrylovFactorization)`](@ref) や、既存の因子分解を長さ `k` に縮小するための [`shrink!(::KrylovFactorization, k)`](@ref) も参照してください。 ```
