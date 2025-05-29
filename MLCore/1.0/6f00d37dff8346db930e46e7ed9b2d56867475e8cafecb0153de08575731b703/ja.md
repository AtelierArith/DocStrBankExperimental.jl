```
numobs(data)
```

`data`に含まれる観測の総数を返します。

`data`に`numobs`が定義されていない場合、`Tables.istable(data) == true`のときは行数を返し、それ以外の場合は`length(data)`を返します。

カスタムデータコンテナの著者は、`numobs`の代わりに自分の型に対して`Base.length`を実装するべきです。`numobs`は、`numobs`と`Base.length`の間に違いがある型（多次元配列など）に対してのみ実装されるべきです。

`numobs`はデフォルトで、配列、タプル、名前付きタプル、辞書のネストされた組み合わせをサポートします。

詳細は[`getobs`](@ref)を参照してください。

# 例

```jldoctest
julia> x = (a = [1, 2, 3], b = ones(6, 3)); # 名前付きタプル

julia> numobs(x)
3

julia> x = Dict(:a => [1, 2, 3], :b => ones(6, 3)); # 辞書

julia> numobs(x) 
3
```

すべての内部コンテナは同じ数の観測を持たなければなりません：

```julia
julia> x = (a = [1, 2, 3, 4], b = ones(6, 3));

julia> numobs(x)
ERROR: DimensionMismatch: すべてのデータコンテナは同じ数の観測を持たなければなりません。
Stacktrace:
 [1] _check_numobs_error()
   @ MLCore ~/.julia/dev/MLCore/src/observation.jl:176
 [2] _check_numobs
   @ ~/.julia/dev/MLCore/src/observation.jl:185 [inlined]
 [3] numobs(data::@NamedTuple{a::Vector{Int64}, b::Matrix{Float64}})
   @ MLCore ~/.julia/dev/MLCore/src/observation.jl:190
 [4] top-level scope
   @ REPL[13]:1
```
