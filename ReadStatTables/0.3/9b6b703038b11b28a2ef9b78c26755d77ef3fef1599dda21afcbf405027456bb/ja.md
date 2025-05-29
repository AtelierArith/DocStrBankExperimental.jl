```
LabeledArray{V, N, A<:AbstractArray{V, N}, K} <: AbstractArray{LabeledValue{V, K}, N}
```

値ラベルに関連付けられた要素を持つ `N` 次元の密な配列。

`LabeledArray` は、Stata のような統計ソフトウェアで値ラベルが達成する機能に似た機能を提供します。REPL に印刷されると、`LabeledArray` は値ラベルの配列のように見えます。しかし、実際には、型 `A` の配列に格納されているのは、型 `V` の基礎となる値のみです。関連付けられた値ラベルは、型 `Dict{K, String}` の辞書から検索されます。値 `v` が辞書のキーと等しくない場合 (`==`)、`string(v)` が値ラベルとして取られます。型 [`LabeledValue{V, K}`](@ref) の要素は、取得されるときにのみ遅延的に構築されます。

`LabeledArray` の基礎となる値の配列には、[`refarray`](@ref) を介してアクセスできます。`LabeledArray` に関連付けられた値ラベルの辞書には、[`getvaluelabels`](@ref) を介してアクセスできます。各要素の値ラベルに対するイテレータは、`LabeledArray` と同じ配列の形状を持ち、[`valuelabels`](@ref) を介して取得できます。

`LabeledArray` を含む等価比較 (`==`) は、基礎となる値のみを比較し、値ラベルは無視されます。値ラベルを比較するには、最初に [`valuelabels`](@ref) を使用してラベルを取得してください。

`push!`、`insert!`、`deleteat!`、`append!` などの追加の配列メソッドは、[`LabeledVector`](@ref) に対してサポートされています。これらは、[`refarray`](@ref) を介して取得された基礎となる値の配列に適用され、値ラベルの辞書を変更しません。

便利のために、`LabeledArray(x::AbstractArray{<:AbstractString}, ::Type{T}=Int32)` は、指定された型の整数で文字列値をエンコードすることによって、文字列配列を `LabeledArray` に変換します（デフォルトは `Int32`）。

# 例

```jldoctest
julia> lbls1 = Dict(1=>"a", 2=>"b");

julia> lbls2 = Dict(1.0=>"p", 2.0=>"q");

julia> x = LabeledArray([0, 1, 2], lbls1)
3-element LabeledVector{Int64, Vector{Int64}, Int64}:
 0 => 0
 1 => a
 2 => b

julia> y = LabeledArray([0.0, 1.0, 2.0], lbls2)
3-element LabeledVector{Float64, Vector{Float64}, Float64}:
 0.0 => 0.0
 1.0 => p
 2.0 => q

julia> x == y
true

julia> x == 0:2
true

julia> refarray(x)
3-element Vector{Int64}:
 0
 1
 2

julia> getvaluelabels(x)
Dict{Int64, String} with 2 entries:
  2 => "b"
  1 => "a"

julia> valuelabels(x) == ["0", "a", "b"]
true

julia> push!(x, 2)
4-element LabeledVector{Int64, Vector{Int64}, Int64}:
 0 => 0
 1 => a
 2 => b
 2 => b

julia> push!(x, 3 => "c")
5-element LabeledVector{Int64, Vector{Int64}, Int64}:
 0 => 0
 1 => a
 2 => b
 2 => b
 3 => c

julia> deleteat!(x, 4:5)
3-element LabeledVector{Int64, Vector{Int64}, Int64}:
 0 => 0
 1 => a
 2 => b

julia> append!(x, [0, 1, 2])
6-element LabeledVector{Int64, Vector{Int64}, Int64}:
 0 => 0
 1 => a
 2 => b
 0 => 0
 1 => a
 2 => b

julia> v = ["a", "b", "c"];

julia> LabeledArray(v, Int16)
3-element LabeledVector{Int16, Vector{Int16}, Union{Char, Int32}}:
 1 => a
 2 => b
 3 => c
```
