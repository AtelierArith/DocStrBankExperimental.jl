```
@multilinear f
@multilinear f f0
```

このマクロは、関数 `f`（または `f0`）の多重線形拡張を定義します。これは `@linear f` に類似しています。新しいメソッドは、項と線形結合の両方を引数として受け入れます。すべての引数を線形結合として線形に展開し、各項の組み合わせに対して `f` を呼び出します。`f0` が指定されている場合は、項を評価するために `f0` が代わりに呼び出されます。

新しいメソッドは常に線形結合（型 `Linear` で、`addto` キーワードによってオーバーライドされない限り）を返します。項の型は、引数としての項を持つ `f`（または `f0`）の戻り値の型から推論されます。係数の型は、すべての `AbstractLinear` 引数の係数型を昇格させることによって計算されます。`f`（または `f0`）が項引数に対して線形結合を返す場合、その係数型も考慮されます。

すべての項と線形結合の可能な組み合わせをキャッチするために、`@multilinear f` と `@multilinear f f0` は、**すべての**引数型に一致する単一の新しいメソッド `f(x...; kw...)` を定義します。（これは `@linear` とは異なります。）したがって、`f0` が与えられていない場合、項を評価するための `f` のメソッドは非汎用的なシグネチャを持たなければなりません。代わりにシグネチャが `f(x::Any...)` である場合、このメソッドは上書きされ、`f` が呼び出されるとエラーが発生します。

`@multilinear` によって定義された新しいメソッドは、`@linear` で議論されたすべてのキーワード引数を受け入れます。未知のキーワード引数は、項評価の呼び出しに渡されます。マクロ `@linear_kw` は線形関数に対して機能します。

`@multilinear` の二引数バージョンが使用される場合、通常 `f` の他のメソッドは存在しません。したがって、この場合 `f` はすべての引数に対して線形結合を返します。すべての引数が項であり、かつ `f0` が項を返す場合、係数型は `LinearCombinations.DefaultCoefftype` です。一引数バージョンの場合、上記で議論されたように、少なくとも1つの他のメソッドが存在しなければなりません。したがって、`f` はすべての引数に対して線形結合を返さない場合があります。

[`@linear`](@ref)、[`@linear_kw`](@ref)、[`LinearCombinations.DefaultCoefftype`](@ref) も参照してください。

# 例

## 項を返す関数の双線形拡張

```jldoctest multilinear
julia> f(x::Char, y::String) = x*y; @multilinear f

julia> a, b = Linear('x' => 1, 'y' => 2), Linear("z" => 1.0, "w" => -1.0)
(Linear{Char, Int64}('x' => 1, 'y' => 2), Linear{String, Float64}("w" => -1.0, "z" => 1.0))

julia> f(a, "z")
Linear{String, Int64} with 2 terms:
2*"yz"+"xz"

julia> f('x', b)
Linear{String, Float64} with 2 terms:
-"xw"+"xz"

julia> f(a, b)
Linear{String, Float64} with 4 terms:
-"xw"+2.0*"yz"-2.0*"yw"+"xz"
```

## 線形結合を返す関数の双線形拡張

```jldoctest multilinear
julia> f(x::Char, y::String) = Linear(x*y => BigInt(1), y*x => BigInt(-1)); @multilinear f

julia> f(a, b)   # 同じ a と b
Linear{String, BigFloat} with 8 terms:
-2.0*"zy"-"xw"-"zx"+2.0*"yz"+"wx"-2.0*"yw"+"xz"+2.0*"wy"

julia> typeof(ans)
Linear{String, BigFloat}
```

## 関数の多重線形拡張

```jldoctest multilinear
julia> g(xs::Union{Char,String}...) = *(xs...); @multilinear g

julia> g(a)   # 同じ a と b
Linear{String, Int64} with 2 terms:
"x"+2*"y"

julia> g(a, b)
Linear{String, Float64} with 4 terms:
-"xw"+2.0*"yz"-2.0*"yw"+"xz"

julia> g(a, b, a)
Linear{String, Float64} with 8 terms:
-"xwx"+"xzx"+4.0*"yzy"+2.0*"xzy"+2.0*"yzx"-2.0*"ywx"-2.0*"xwy"-4.0*"ywy"
```

## `@multilinear` の二引数バージョンを使用した多重線形拡張

```jldoctest multilinear
julia> @multilinear(h, *)

julia> h(a, b; coeff = 2)   # 同じ a と b
Linear{String, Float64} with 4 terms:
-2.0*"xw"+4.0*"yz"-4.0*"yw"+2.0*"xz"
```
