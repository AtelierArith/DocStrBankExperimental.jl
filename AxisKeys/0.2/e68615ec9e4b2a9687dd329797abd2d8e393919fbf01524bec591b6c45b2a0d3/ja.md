```
Near(val)
Interval(lo, hi)
```

これらのセレクタは `axiskeys(A)` を使用したルックアップを修正します： `B(time = Near(3))` は、名前付き次元 `:time` の最小 `abs(t-3)` を持つエントリを1つ一致させます。 `C("cat", Interval(10,20))` は、すべてのエントリを `10 <= iter <= 20` で一致させます。

`Interval` は IntervalSets.jl からのもので、これを使用すると `lo .. hi` や `mid ± δ` と書くこともできます。

```
==(val)
<(val)
```

任意の関数も同様に使用できます。例えば、C(!=("dog"), <=(33)) のようにです。これらは最終的に `findall(==(val), axiskeys(A,d))` を呼び出します。

`Base.Fix2` 型の関数や `Selector` も、型によって次元を選択することを可能にします： `A(<=(3.1))` は、 `map(eltype, axiskeys(A))` の中で `typeof(3.1)` に一致するものが1つだけであれば機能します。

# 例

```jldoctest
julia> v = KeyedArray(Symbol.('a':'e'), 10:10:50)
1次元の KeyedArray(...) キー付き:
↓   5要素の StepRange{Int64,...}
およびデータ、5要素の Vector{Symbol}:
 (10)  :a
 (20)  :b
 (30)  :c
 (40)  :d
 (50)  :e

julia> v[Near(33)]
:c

julia> v[==(30)]  # このキーに一致するすべて
1次元の KeyedArray(...) キー付き:
↓   1要素の Vector{Int64}
およびデータ、1要素の Vector{Symbol}:
 (30)  :c

julia> v[Interval(17, 31)]
1次元の KeyedArray(...) キー付き:
↓   2要素の StepRange{Int64,...}
およびデータ、2要素の Vector{Symbol}:
 (20)  :b
 (30)  :c

julia> m = wrapdims(hcat(v,v), x=nothing, y=[:left, :right]);

julia> m(<(30))  # 型によって1次元を選択し、ビューを作成
2次元の KeyedArray(NamedDimsArray(...)) キー付き:
↓   x ∈ 2要素の StepRange{Int64,...}
→   y ∈ 2要素の Vector{Symbol}
およびデータ、2×2 ビュー(::Matrix{Symbol}, 1:2, :) の eltype Symbol:
       (:left)  (:right)
 (10)    :a       :a
 (20)    :b       :b
```
