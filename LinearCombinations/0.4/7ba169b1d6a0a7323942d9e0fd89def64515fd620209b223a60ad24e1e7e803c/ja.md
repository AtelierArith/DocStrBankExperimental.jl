```
@linear_kw 関数定義
```

`@linear_kw` は関数定義をスキャンし、キーワード `coefftype`、`addto`、`coeff` および `sizehint` を `LinearCombinations` パッケージに知らしめます。これにより、高性能なコードを書くことができます。すべてのキーワードが存在する必要はありません。ただし、`addto` と `coeff` は一緒に使用される場合にのみ効果があります。

さらに [`LinearCombinations.has_coefftype`](@ref)、[`LinearCombinations.has_addto_coeff`](@ref)、[`LinearCombinations.has_isfiltered`](@ref)、[`LinearCombinations.has_sizehint`](@ref)、[`LinearCombinations.unval`](@ref) を参照してください。

# 例

次の2つの関数を考えてみましょう：

```jldoctest addto-coeff; output = false
f(x::Char) = Linear(uppercase(x) => 1, x => -1)

@linear f

using LinearCombinations: unval   # Val 引数をアンラップします

@linear_kw 関数 g(x::Char;
        coefftype = Int,
        addto = zero(Linear{Char,unval(coefftype)}),
        coeff = 1)
    addmul!(addto, uppercase(x), coeff)
    addmul!(addto, x, -coeff)
    addto
end

@linear g

# 出力

g (汎用関数で2つのメソッドを持つ)
```

線形拡張は機能的に同等ですが、`g` は `f` よりもはるかに速くなります。

```jldoctest addto-coeff
julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} で2項を持つ:
'x'+2*'y'

julia> f(a; coefftype = Float64, coeff = 2)
Linear{Char, Float64} で4項を持つ:
4.0*'Y'-2.0*'x'-4.0*'y'+2.0*'X'

julia> g(a; coefftype = Float64, coeff = 2)
Linear{Char, Float64} で4項を持つ:
4.0*'Y'-2.0*'x'-4.0*'y'+2.0*'X'
```

キーワードが登録されているかどうかをテストします：

```jldoctest addto-coeff
julia> using LinearCombinations: has_coefftype, has_addto_coeff, has_sizehint

julia> has_coefftype(g, Char), has_addto_coeff(g, Char), has_sizehint(g, Char)
(true, true, false)
```
