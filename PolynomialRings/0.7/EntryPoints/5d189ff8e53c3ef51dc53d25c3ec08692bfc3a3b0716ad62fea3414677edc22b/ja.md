```
@ring! ℚ[x,y]
```

指定された多項式環を定義して返し、変数名をその生成元にバインドします。

現在サポートされている環は次のとおりです: ℚ (`Rational{BigInt}`)、ℤ (`BigInt`)、ℝ (`BigFloat`) および ℂ (`Complex{BigFloat}`)。

注意: `@ring!` は環を返し、変数を注入します。マクロ `@ring` は環のみを返します。

異なる係数環が必要な場合や、非デフォルトの単項式順序または指数整数型を指定する必要がある場合は、代わりに `polynomial_ring` を使用してください。

# 例

```jldoctest
julia> using PolynomialRings

julia> @ring! ℚ[x,y];

julia> x^3 + y
x^3 + y
```

# 参照

`polynomial_ring`
