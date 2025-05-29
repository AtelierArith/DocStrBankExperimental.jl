```
signature(sig::Type{<:Tuple})
```

`ExprTools.signature(::Method)`と似ていますが、Methodではなく基盤となるシグネチャ型タプルに対して行います。`sig`がメソッドの型シグネチャを表すタプル型である場合、これは`ExprTools.combinedef`に渡してその関数を定義するための辞書を生成します。ただし、最初に辞書の`:body`キーに値を割り当てる必要があります。

出力の品質は、名前の一致などに関して`signature(::Method)`ほど高くはありませんが、すべての重要な情報は含まれています。また、型タプルは他の目的に対して一般的に操作しやすいです。

例

```julia
julia> signature(Tuple{typeof(identity), Any})
Dict{Symbol, Any} with 2 entries:
  :name => :(op::typeof(identity))
  :args => Expr[:(x1::Any)]

julia> signature(Tuple{typeof(+), Vector{T}, Vector{T}} where T<:Number)
Dict{Symbol, Any} with 3 entries:
  :name        => :(op::typeof(+))
  :args        => Expr[:(x1::Array{var"##T#5492", 1}), :(x2::Array{var"##T#5492", 1})]
  :whereparams => Any[:(var"##T#5492" <: Number)]
```

# キーワード

  * `extra_hygiene=false`: `true`に設定すると、`UnionAll`内の`TypeVar`に対して名前のハイジーンを強制し、`gensym`を介してそれぞれを一意の名前で再生成します。実際には、スコープが設定されているため、漏れないはずです。しかし、関数の型変数と衝突した場合に漏れるという長年の[Juliaのバグ](https://github.com/JuliaLang/julia/issues/39876)があります。
