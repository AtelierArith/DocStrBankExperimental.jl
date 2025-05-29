```
L(xc::Pair...; is_filtered = false; kw...) where L <: AbstractLinear
L(itr; is_filtered = false; kw...) where L <: AbstractLinear
```

`AbstractLinear{T,R}` は、項の型 `T` と係数の型 `R` を持つすべての線形結合のスーパークラスです。

サブタイプ `L <: AbstractLinear` のコンストラクタは、与えられた項-係数ペアの形式 `x => c` から型 `L` の線形結合を構築します。ここで `x` は項で、`c` は係数です。また、イテレータ `itr` によって提供されたペアからも構築できます。すべての項と係数を選択した項の型および係数の型にそれぞれ変換できる必要があります。

項の型も係数の型も具体的である必要はありません。（もちろん、具体的な型はより良いパフォーマンスをもたらします。）係数の型と、場合によっては項の型が指定されていない場合、コンストラクタは `promote_type`（係数用）および `promote_typejoin`（項用）を使用してそれらを決定しようとします。

同じ項を持つ2つ以上の項-係数ペアが与えられた場合、対応する係数は合計されます。これは、同じキーを持つ以前のペアを上書きする辞書とは異なります。ただし、実装された動作は線形結合にとってより有用です。

特定のアプリケーションでは、項と係数は線形結合に格納される前に `linear_filter` および `termcoeff` で処理できます。キーワード引数 `is_filtered` は、各項に対して `linear_filter` が呼び出されるかどうかを制御します。

デフォルトでは、線形結合は限られた数の項を持つ人間が読みやすい形式で表示されます。専用の `show` メソッドは、線形結合のすべての項を表示するか、Julia が入力として解析できる式を返します。以下の例を参照してください。

[`Linear`](@ref)、[`DenseLinear`](@ref)、[`Linear1`](@ref)、[`linear_filter`](@ref)、[`LinearCombinations.termcoeff`](@ref)、`Base.show` も参照してください。

# 例

```jldoctest abstractlinear
julia> Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> Linear(x => c for (c, x) in enumerate('u':'z'))
Linear{Char, Int64} with 6 terms:
3*'w'+2*'v'+4*'x'+'u'+5*'y'+6*'z'

julia> Linear{Char,Int}('x' => 1, 'y' => Int8(0), 'x' => 3.0)
Linear{Char, Int64} with 1 term:
4*'x'

julia> a = Linear('x' => BigInt(1), "yz" => 2.0)
Linear{Any, BigFloat} with 2 terms:
'x'+2.0*"yz"
```

線形結合を反復処理すると、すべての非ゼロの項-係数ペアが得られます。したがって、線形結合自体を `AbstractLinear` コンストラクタへの引数として使用できます。

```jldoctest abstractlinear
julia> Linear{Union{Char,String}}(a)   # 同じ a
Linear{Union{Char, String}, BigFloat} with 2 terms:
'x'+2.0*"yz"
```

線形結合を表示するさまざまな形式。

```jldoctest
julia> a = Linear(x => 1 for x in 'a':'z')
Linear{Char, Int64} with 26 terms:
'n'+'f'+'w'+'d'+'e'+'o'+'h'+'j'+'i'+'k'+'r'+'s'+'t'+'q'+'y'+'a'+'c'+'p'+'m'+'z'±⋯

julia> show(stdout, MIME"text/plain"(), a)  # すべての項
Linear{Char, Int64} with 26 terms:
'n'+'f'+'w'+'d'+'e'+'o'+'h'+'j'+'i'+'k'+'r'+'s'+'t'+'q'+'y'+'a'+'c'+'p'+'m'+'z'+'g'+'v'+'l'+'u'+'x'+'b'

julia> b = Linear('a' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'a'+2*'y'

julia> show(b)  # 入力として解析可能
Linear{Char, Int64}('a' => 1, 'y' => 2)
```
