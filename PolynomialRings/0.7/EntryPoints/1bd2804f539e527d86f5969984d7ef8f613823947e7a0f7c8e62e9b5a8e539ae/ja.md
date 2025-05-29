```
@ring ℚ[x,y]
```

指定された多項式環を定義して返します。

現在サポートされている環は次のとおりです: ℚ (`Rational{BigInt}`)、ℤ (`BigInt`)、ℝ (`BigFloat`) および ℂ (`Complex{BigFloat}`)。

注意: `@ring!` は環を返し、変数を周囲のスコープに注入します。マクロ `@ring` は環のみを返します。

異なる係数環が必要な場合や、デフォルトでない単項式順序や指数整数型を指定する必要がある場合は、代わりに `polynomial_ring` を使用してください。

# 例

```jldoctest
julia> using PolynomialRings

julia> @ring ℚ[x,y]
@ring(ℚ[x,y])
```

# 参照

`polynomial_ring` `@ring!`
