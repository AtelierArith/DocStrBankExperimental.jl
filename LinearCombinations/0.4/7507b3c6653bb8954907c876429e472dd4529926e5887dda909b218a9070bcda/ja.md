```
@linear f
```

このマクロは、関数（または呼び出し可能なオブジェクト）`f`の線形拡張を定義します。より具体的には、`f(a::AbstractLinear{T,R}; kw...) where {T,R}`という新しいメソッドを定義し、`a`に現れるすべての項-係数ペア`x => c`について、`c*f(x)`を合計することによって得られる線形結合を返します。

新しいメソッドは、以下のキーワード引数を認識します：

  * `coefftype`:   このオプションのキーワード引数は、キーワード引数`addto`が存在しない場合に、`f(a)`によって返される線形結合の係数型を指定します。`coefftype`が指定されていない場合、かつ`f(x::T)`が項（線形結合ではない）である場合、`coefftype`は`R`に設定されます。もし`f(x::T) <: AbstractLinear`であり、係数型が`S`である場合、`promote_type(R, S)`が新しい係数型として選ばれます。`addto`キーワードが存在する場合、`coefftype`は無視されます。

    Juliaがキーワード引数を扱う方法のため、`f(a; coefftype = Int)`の形式は型安定ではありません。型安定性は、`f(a; coefftype = Val(Int))`と言うことで達成できます。
  * `addto::AbstractLinear`:   指定された場合、すべての項`c*f(x)`の合計が`addto`に加算され、結果が返されます。これにより、`AbstractLinear`引数で`f`が呼び出されるたびに新しい線形結合を割り当てることを避けます。`addto`のデフォルト値は`Linear{U,coefftype}`です。ここで`U`は、`f(x::T)`の返り値の型であり、この返り値の型が`AbstractLinear`のサブタイプでない場合、返り値の項の型です。
  * `coeff`:   このオプションのキーワード引数は、`f(a)`のスカラー倍を効率的に計算することを可能にします。より正確には、`f(a; coeff = c)`は`c*f(a)`を返し、`f(a; addto = b, coeff = c)`は`c*f(a)`を`b`に加算し、この新しい値を返します。
  * `sizehint::Bool = true`:   `f`の新しいメソッドは、`addto`に対して新しい項のためのスペースを事前に割り当てるために`sizehint!`を呼び出すことがあります。このキーワード引数は、事前割り当てをオフにすることを許可します。

他のすべてのキーワード引数は`f(x)`に渡されます。マクロ`@linear_kw`を使用すると、`f(a)`が上記の特別なキーワード引数を`f(x)`に渡すことができます。

他にも[`@multilinear`](@ref)、[`sizehint!`](@ref)、[`@linear_kw`](@ref)、[`keeps_filtered`](@ref)を参照してください。

# 例

## 項を返す関数の線形拡張

```jldoctest linear
julia> f(x) = uppercase(x); @linear f
f (generic function with 2 methods)

julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> f(a)
Linear{Char, Int64} with 2 terms:
2*'Y'+'X'

julia> f(a; coefftype = Float64)
Linear{Char, Float64} with 2 terms:
2.0*'Y'+'X'

julia> b = Linear('z' => 3); f(a; addto = b, coeff = -1); b
Linear{Char, Int64} with 3 terms:
-2*'Y'-'X'+3*'z'
```

## 線形結合を返す関数の線形拡張

```jldoctest linear
julia> g(x) = Linear(x*x => 1.0, string(x) => -1.0); @linear g
g (generic function with 2 methods)

julia> g("x"), g("")
(Linear{String, Float64}("xx" => 1.0, "x" => -1.0), Linear{String, Float64}())

julia> g(a)   # 同じa
Linear{String, Float64} with 4 terms:
"xx"-"x"+2.0*"yy"-2.0*"y"

julia> g(a; coefftype = Val(Int), coeff = 3.0)
Linear{String, Int64} with 4 terms:
3*"xx"-3*"x"+6*"yy"-6*"y"
```

## 呼び出し可能なオブジェクトの線形拡張

```jldoctest linear
julia> struct P y::String end

julia> (p::P)(x) = p.y*x*p.y; @linear p::P

julia> p = P("w"); p(a)   # 同じa
Linear{String, Int64} with 2 terms:
"wxw"+2*"wyw"
```
