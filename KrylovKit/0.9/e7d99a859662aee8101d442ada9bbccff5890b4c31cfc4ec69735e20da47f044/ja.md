```
struct GKLIterator{F,TU,O<:Orthogonalizer}
GKLIterator(f, u₀, [orth::Orthogonalizer = KrylovDefaults.orth, keepvecs::Bool = true])
```

一般的な線形写像 `f::F` と初期ベクトル `u₀::TU` を受け取り、それに基づいて拡張する `GKLFactorization` を生成するイテレータです。特に、`GKLIterator` は [Golub-Kahan-Lanczos 二重対角化手法](http://www.netlib.org/utk/people/JackDongarra/etemplates/node198.html) を実装しています。ただし、この実装は線形写像 `f` のコドメイン内のベクトル `u₀` から始まるため、正規化後には `U` の最初の列として終わります。

引数 `f` は行列、2つの関数のタプル（最初の関数が通常の作用を表し、2番目が随伴作用を表す）、または2つの引数を受け取る関数であり、最初の引数が線形写像を適用するベクトル、2番目の引数が通常の作用の場合は `Val(false)`、随伴作用の場合は `Val(true)` です。フラグは `Val` 型であり、線形写像のドメインとコドメインのベクトルが異なる型を持つ場合に型の安定性を確保します。

オプションの引数 `orth` は使用する [`Orthogonalizer`](@ref) を指定します。[`KrylovDefaults`](@ref) のデフォルト値は [`ModifiedGramSchmidtIR`](@ref) を使用することであり、再直交化ステップを使用する可能性があります。

`GKLIterator` のインスタンスを反復する際に生成される値は、[`GKLFactorization`](@ref) のインスタンス `fact` であり、これをすぐに [`basis(fact, Val(:U))`](@ref)、[`basis(fact, Val(:V))`](@ref)、[`rayleighquotient`](@ref)、[`residual`](@ref)、[`normres`](@ref)、[`rayleighextension`](@ref) に分解できます。例えば、次のようにします。

```julia
for (U, V, B, r, nr, b) in GKLIterator(f, u₀)
    # 何かをする
    nr < tol && break # 一般的な停止基準
end
```

イテレータは、型 `T` のオブジェクトの基礎となるベクトル空間の次元を知らないため、残差ノルム `nr` が機械精度 `eps(typeof(nr))` を下回るまでクリロフ部分空間を拡張し続けます。

`GKLIterator` の内部状態は、対応する `GKLFactorization` と同じです。ただし、Julia の Base の反復インターフェース（`Base.iterate` を使用）では状態が変更されないことが要求されるため、次の反復ステップごとに `deepcopy` が生成されます。

代わりに、次のインターフェースを使用して `GKLFactorization` をその場で変更することもできます。例えば、上記の同じ例に対して

```julia
iterator = GKLIterator(f, u₀)
factorization = initialize(iterator)
while normres(factorization) > tol
    expand!(iterator, factorization)
    U, V, B, r, nr, b = factorization
    # 何かをする
end
```

ここで、[`initialize(::GKLIterator)`](@ref) は長さ1の最初の GKL 因子分解を生成し、`expand!(::GKLIterator, ::GKLFactorization)`(@ref) は因子分解をその場で拡張します。また、既存の因子分解を初期化するための [`initialize!(::GKLIterator, ::GKLFactorization)`](@ref) や、既存の因子分解を長さ `k` に縮小するための [`shrink!(::GKLIterator, k)`](@ref) も参照してください。 ```
