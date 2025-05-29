```
@polyvar var [var...]
```

与えられた変数で多項式環を定義し、それらを周囲のスコープに注入します。

これは `@ring! Int[var...]` と同等です。

異なる係数環が必要な場合や、デフォルトでない単項式順序や指数整数型を指定する必要がある場合は、代わりに `@ring!` または `polynomial_ring` を使用してください。

# 例

```jldoctest
julia> using PolynomialRings

julia> @polyvar x y;

julia> x + 3y
x + 3*y

julia> @polyvar ε[];

julia> 1 + ε()*x + ε()*y
ε[1]*x + ε[2]*y + 1
```

# 参照

`polynomial_ring` `@ring!`
