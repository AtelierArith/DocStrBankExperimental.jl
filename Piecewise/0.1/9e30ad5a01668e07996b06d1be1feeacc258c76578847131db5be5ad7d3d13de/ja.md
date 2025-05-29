```
Formula([name::String,] params::Integer, value::Function
    [, check::Function] [, scale::Function] [, mirror::Function])
```

`Formula`オブジェクトのコンストラクタで、オプションの名前と、`params >= 0`の場合は正確に`params`、`params < 0`の場合は最大で`-params`の数のパラメータを持ちます。数式の値は関数`value(::Real, ::Vector{Any})`によって設定されます。オプションの関数`check(a::Vector{Any}, domain::Tuple{Real, Real}, included::Tuple{Bool, Bool}, danger::Bool, fatal::Bool)`は、関数`value(x, a)`が`domain`と`included`で指定されたドメイン内で有効かどうかに応じて`true`または`false`を返さなければなりません（`Piece`](@ref)を参照）。警告は`danger`が`true`の場合にのみ`check`によって発行され、エラーは`fatal`が`true`の場合にのみスローされなければなりません。オプションの関数`scale(a::Vector{Any}, s::Number)`は、数式を`s`で乗算した後のパラメータを返さなければなりません。オプションの関数`mirror(a::Vector{Any})`は、$x=0$を通る数式の偶数反射後のパラメータを返さなければなりません。

## フィールド

  * `name::String`
  * `params::Integer`
  * `value::Function`
  * `check::Function`
  * `scale::Function`
  * `mirror::Function`

## 例

これは平方根の特異点を作成します：

```julia-repl
julia> srs(x, a) = a[2] * sqrt(x - a[1])
julia> function srs(a, domain, included, danger, fatal)
           t = domain[1] > a[1] || (domain[1] == a[1] && ! included[1])
           !t && fatal && throw(ArgumentError("Singularity must be at left of domain."))
           t || return false
           t = a[2] >= 0
           !t && danger && @warn "Negative singularity in domain $(domain)."
           return true
       end
julia> F = Formula("SRS", 2, srs, srs)
Formula("SRS", 2, srs, srs)

julia> F.check([1, 1], (0, 2), (true, true), true, false)
false

julia> F.check([-1, -1], (0, 2), (true, true), true, false)
┌ Warning: Negative singularity in domain (0, 2).
└ @ Main REPL[3]:6
true
```
