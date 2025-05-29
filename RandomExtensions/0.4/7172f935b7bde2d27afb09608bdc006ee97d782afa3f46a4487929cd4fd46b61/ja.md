```
rand([rng=GLOBAL_RNG], [S], [C...]) # RandomExtensions
```

指定された値の集合 `S` からランダムな要素またはランダムな要素のコレクションを選択します。`S` は次のいずれかです。

  * インデックス可能なコレクション（例えば `1:n` や `['x','y','z']`）、
  * `AbstractDict` または `AbstractSet` オブジェクト、
  * 文字列（文字のコレクションと見なされます）、または
  * 型：選択する値の集合は、整数の場合 `typemin(S):typemax(S)` に相当します（これは `BigInt` には適用されず、浮動小数点数の場合は $[0, 1)$ に適用されません）；
  * `Distribution` オブジェクト、例えば正規分布のための `Normal()`（`randn()` のように）、または範囲 $[10.0, 20.0)$ の均一な `Float64` 数のための `CloseOpen(10.0, 20.0)`；
  * `make` オブジェクト、例えば `make(Pair, S1, S2)` や `make(Complex, S1, S2)` のように、ここで `S1` と `S2` は上記のいずれかの仕様です；`Pair` または `Complex` は具体的な型としてオプションで指定できます。例えば `make(ComplexF64, 1:3, Int)` は `Complex{Int}` の代わりに `ComplexF64` を生成します。

`S` は通常 `Float64` にデフォルト設定されています。

`C...` が指定されていない場合、`rand` はスカラーを生成します。そうでない場合、`C` は次のいずれかです。

  * 整数の集合、または `Int` のタプルで、生成する `Array` の次元を指定します；
  * `(Array, dims...)`：上記と同じですが、`Array` が明示的に指定されています；
  * `(p::AbstractFloat, m::Integer, [n::Integer])`：次元 `(m, n)` のスパース配列を生成し、任意の要素が非ゼロである確率は独立して `p` によって与えられます；
  * `(String, [n=8])`：長さ `n` のランダムな `String` を生成します；生成された文字列は `randstring` のような事前定義されたセットから取られた `Char` で構成され、`S` パラメータで指定できます；
  * `(Dict, n)`：長さ `n` の `Dict` を生成します；`Dict` が型パラメータなしで与えられた場合、`S` を指定する必要があります；
  * `(Set, n)` または `(BitSet, n)`：長さ `n` の集合を生成します；
  * `(BitArray, dims...)`：指定された次元の `BitArray` を生成します。

`Array`、`Dict`、および `Set` に対して、`Set{Float64}` のように、より具体的な型を指定して、`S` パラメータに関係なく結果の型を強制することができます。特に、`S` がない場合、コンテナの型パラメータは `S` の役割を果たします；例えば、`rand(Dict{Int,Float64}, n)` は `rand(make(Pair, Int, Float64), Dict, n)` と同等です。

# 例

```julia-repl
julia> rand(Int, 2)
2-element Array{Int64,1}:
 1339893410598768192
 1575814717733606317

julia> rand(MersenneTwister(0), Dict(1=>2, 3=>4))
1=>2

julia> rand("abc", String, 12)
"bccaacaabaac"

julia> rand(1:10, Set, 3)
Set([3, 8, 6])

julia> rand(1:10, Set{Float64}, 3)
Set([10.0, 5.0, 6.0])
```

!!! note
    `rand(rng, s::Union{AbstractDict,AbstractSet})` の複雑さは `s` の長さに対して線形であり、定数の複雑さを持つ最適化されたメソッドが利用可能な場合（`Dict`、`Set`、および `BitSet` の場合）を除きます。数回以上の呼び出しには、代わりに `rand(rng, collect(s))` を使用するか、適切に `rand(rng, Dict(s))` または `rand(rng, Set(s))` を使用してください。

