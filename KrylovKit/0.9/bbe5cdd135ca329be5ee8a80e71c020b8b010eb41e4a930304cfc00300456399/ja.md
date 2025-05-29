```
struct LanczosIterator{F,T,O<:Orthogonalizer} <: KrylovIterator{F,T}
LanczosIterator(f, v₀, [orth::Orthogonalizer = KrylovDefaults.orth, keepvecs::Bool = true])
```

線形マップ `f::F`（実対称または複素エルミートであると仮定）と初期ベクトル `v₀::T` を受け取り、それに基づいて拡張する `LanczosFactorization` を生成するイテレータです。特に、`LanczosIterator` は [ランチョス反復法](https://en.wikipedia.org/wiki/Lanczos_algorithm) スキームを使用して、次第に拡張されるランチョス因子分解を構築します。線形マップが一般的な呼び出し可能オブジェクトや関数としてエンコードされている場合、`f` が対称またはエルミートであるかどうかを直接テストすることはできませんが、`inner(v, f(v))` の虚部が無視できるほど小さいかどうかがテストされます。

引数 `f` は行列であるか、単一の引数 `v` を受け取る関数であり、`f(v)` がベクトル `v` に対する線形マップの作用を実装します。

オプションの引数 `orth` は使用する [`Orthogonalizer`](@ref) を指定します。[`KrylovDefaults`](@ref) のデフォルト値は [`ModifiedGramSchmidtIR`](@ref) を使用することで、再直交化ステップを使用する可能性があります。古いベクトルをクリロフ部分空間から破棄するには、最終引数 `keepvecs` を `false` に設定します。ただし、これは再直交化に依存しない `orth` アルゴリズム（例えば `ClassicalGramSchmidt()` や `ModifiedGramSchmidt()`）が使用されている場合にのみ可能です。その場合、イテレータは厳密にランチョスの三項再帰関係を使用します。

`LanczosIterator` のインスタンスを反復する際に生成される値は [`LanczosFactorization`](@ref) のインスタンスであり、例えば次のように [`basis`](@ref)、[`rayleighquotient`](@ref)、[`residual`](@ref)、[`normres`](@ref)、および [`rayleighextension`](@ref) に即座に分解できます。

```julia
for (V, B, r, nr, b) in LanczosIterator(f, v₀)
    # 何かをする
    nr < tol && break # 一般的な停止基準
end
```

ただし、`LanczosIterator` で `keepvecs=false` の場合、基底 `V` を抽出することはできません。

イテレータは、型 `T` のオブジェクトの基礎となるベクトル空間の次元を知らないため、残差ノルム `nr` が機械精度 `eps(typeof(nr))` を下回るまでクリロフ部分空間を拡張し続けます。

`LanczosIterator` の内部状態は戻り値と同じであり、すなわち対応する `LanczosFactorization` です。ただし、Julia の Base イテレーションインターフェース（`Base.iterate` を使用）では状態が変更されないことが要求されるため、次のイテレーションステップごとに `deepcopy` が生成されます。

代わりに、次のインターフェースを使用して `KrylovFactorization` をその場で変更することもできます。例えば、上記の同じ例に対して

```julia
iterator = LanczosIterator(f, v₀)
factorization = initialize(iterator)
while normres(factorization) > tol
    expand!(iterator, factorization)
    V, B, r, nr, b = factorization
    # 何かをする
end
```

ここで、[`initialize(::KrylovIterator)`](@ref) は長さ1の最初のクリロフ因子分解を生成し、`expand!(::KrylovIterator, ::KrylovFactorization)`(@ref) はその場で因子分解を拡張します。また、既存の因子分解で初期化するための [`initialize!(::KrylovIterator, ::KrylovFactorization)`](@ref) や、既存の因子分解を長さ `k` に縮小するための [`shrink!(::KrylovFactorization, k)`](@ref) も参照してください。 ```
