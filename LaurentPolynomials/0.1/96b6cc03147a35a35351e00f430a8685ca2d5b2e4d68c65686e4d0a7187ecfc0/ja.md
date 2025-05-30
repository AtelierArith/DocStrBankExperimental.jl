このパッケージは、単変数のローレンツ多項式と単変数の有理数を実装しています。係数は任意の環（非可換のものも含む、例えば `Matrix{Int}`）にすることができます。

2018年の初期の動機は、GAPの多項式をJuliaに簡単に移植する方法を持つことでした。今でも自分のパッケージを持っている理由はいくつかあります：

  * 係数が環にある場合に多項式が適切に動作する必要があり、その場合は擬似除算と部分結果gcdを使用します。
  * 係数の型 `T` が `zero` メソッドを持っているが、`T` 自体は必要な情報を含まない場合に、私の多項式ができるだけうまく機能する必要があります。例として、`BigInt` モジュラスを持つ剰余算があり、これは型の一部にはできません。この理由から、`zero` 多項式は空の係数リストを持たず、ゼロに等しい要素を含むリストを持つため、常にゼロ多項式から型 T のゼロを取得することが可能です。
  * `LaurentPolynomials` は `PuiseuxPolynomials` に使用されるように設計されています。
  * 私の多項式は、`Polynomials` パッケージのものよりも数倍速いことがよくあります。さらに、インターフェースはシンプルで柔軟です。

このパッケージが依存している唯一のパッケージは `LinearAlgebra` で、`exactdiv` 関数を使用しています。

ローレンツ多項式は、係数の型 `T` に対するパラメトリック型 `Pol{T}` です。これらは、型 `T` の係数ベクトルと評価（`Int`）を与えることによって構築されます。評価が `≥0` のものを真の多項式と呼びます。

現在の変数名（`Symbol`）は、REPLやIJulia、Plutoで多項式をきれいに印刷するために使用されます。この名前はグローバルに変更することも、特定の多項式を印刷するためだけに変更することもできます。ただし、多項式はどのシンボルで印刷されるべきかを個別に記録しません。

# 例

```julia-repl
julia> Pol(:q) # 印刷に使用されるシンボルを定義し、Pol([1],1)を返す
Pol{Int64}: q

julia> @Pol q  # q=Pol(:q) と同じ。多項式でセッションを開始するのに便利
Pol{Int64}: q

julia> Pol([1,2]) # 省略した場合、評価は0と見なされる
Pol{Int64}: 2q+1

julia> 2q+1       # 同じ多項式
Pol{Int64}: 2q+1

julia> Pol()   # すべての引数を省略するとPol([1],1)を返す
Pol{Int64}: q

julia> p=Pol([1,2,1],-1) # ここで評価が-1に指定されている
Pol{Int64}: q+2+q⁻¹

julia> q+2+q^-1 # 同じ多項式
Pol{Int64}: q+2+q⁻¹
```

```julia-rep1
julia> print(p) # きれいに印刷できない場合は、読み戻せる出力を提供
Pol([1, 2, 1],-1)

# この時だけ印刷用の変数を変更
julia> print(IOContext(stdout,:limit=>true,:varname=>"x"),p)
x+2+x⁻¹

julia> print(IOContext(stdout,:TeX=>true),p) # TeX形式の出力（Pluto、IJuliaで使用）
q+2+q^{-1}
```

多項式は、`valuation`、`degree`、`getindex` 関数を使用して分解できます。インデックス `p[i]` は、`p` の次数 `i` の係数を返します。

```julia-repl
julia> valuation(p),degree(p)
(-1, 1)

julia> p[0], p[1], p[-1], p[10]
(2, 1, 1, 0)

julia> p[valuation(p):degree(p)]
3-element Vector{Int64}:
 1
 2
 1

julia> p[begin:end]  # 上記の行と同じ
3-element Vector{Int64}:
 1
 2
 1

julia> coefficients(p)  # 再び同じ
3-element Vector{Int64}:
 1
 2
 1
```

係数は任意の環から来ることができます：

```julia-repl
julia> h=Pol([[1 1;0 1],[1 0; 0 1]])
Pol{Matrix{Int64}}: [1 0; 0 1]q+[1 1; 0 1]

julia> h^3
Pol{Matrix{Int64}}: [1 0; 0 1]q³+[3 3; 0 3]q²+[3 6; 0 3]q+[1 3; 0 1]
```

多項式は、評価と次数が `0` の場合に *スカラー* です。`scalar` 関数は、多項式がスカラーである場合は定数係数を返し、そうでない場合は `nothing` を返します。

```julia-repl
julia> Pol(1)
Pol{Int64}: 1

julia> convert(Pol{Int},1) # 同じこと
Pol{Int64}: 1

julia> scalar(Pol(1))
1

julia> convert(Int,Pol(1)) # 同じこと
1

julia> Int(Pol(1))         # 同じこと
1

julia> scalar(q+1) # nothing; convert はエラーを返す
```

配列 `Pol{T}` の異なる型 `T` は、同じ型 `T` に昇格され（関与する `T` に昇格がある場合）、数値は多項式に昇格されます。

通常の算術（`+`、`-`、`*`、`^`、`/`、`//`、`one`、`isone`、`zero`、`iszero`、`==`）が機能します。型 `<:Number` の要素または `Pol{T}` の型 `T` の要素は、係数に対するスカラー操作のためにスカラーと見なされます。

```julia-repl
julia> derivative(p)
Pol{Int64}: 1-q⁻²

julia> p=(q+1)^2
Pol{Int64}: q²+2q+1

julia> p/2
Pol{Float64}: 0.5q²+1.0q+0.5

julia> p//2
Pol{Rational{Int64}}: (1//2)q²+q+1//2

julia> p(1//2) # 1//2でのpの値
9//4

julia> p(0.5)
2.25

julia> Pol([1,2,3],[2.0,1.0,3.0])  # [1,2,3]で[2.0,1.0,3.0]の値を取るpを見つける
Pol{Float64}: 1.5q²-5.5q+6.0
```

多項式はブロードキャストのためのスカラーです。ソートすることができ（評価と係数を比較する `cmp` と `isless` 関数を持っています）、`Dict` のキーとして使用することができます（`hash` 関数を持っています）。

関数 `divrem`、`div`、`%`、`gcd`、`gcdx`、`lcm`、`powermod` は、フィールド上の真の多項式間で動作し、多項式除算を使用します。環上では、`divrem` と `gcd` の代わりに `pseudodiv` と `srgcd` を使用する方が良いです（デフォルトでは、整数多項式間の `gcd` は `srgcd` に委任されます）。

`LinearAlgebra.exactdiv` は、正確な場合に（フィールドまたは環上で）除算を行い、そうでない場合はエラーを返します。

```julia-repl
julia> divrem(q^3+1,2q+1) # 係数をフィールド要素に変更
(0.5q²-0.25q+0.125, 0.875)

julia> divrem(q^3+1,2q+1//1) # 係数がすでにフィールド要素の場合
((1//2)q²+(-1//4)q+1//8, 7//8)

julia> pseudodiv(q^3+1,2q+1) # 擬似除算は環を保持
(4q²-2q+1, 7)

julia> (4q^2-2q+1)*(2q+1)+7 # しかし、戻すと多項式の倍数になる
Pol{Int64}: 8q³+8

julia> LinearAlgebra.exactdiv(q+1,2.0) # LinearAlgebra.exactdiv(q+1,2) はエラーを返す
Pol{Float64}: 0.5q+0.5
```

最後に、`Pol` には、係数に対して操作する `conj`、`adjoint` メソッド、Kazhdan-Lusztig理論に役立つ `positive_part`、`negative_part`、`bar` メソッド、ランダムな多項式を生成する `randpol` メソッドがあります。

多項式を反転することは、有理数 `Frac{Pol{T}}` を取得する方法であり、`Frac` は分数の一般的な型です。有理数は、分子と分母が互いに素な真の多項式になるように正規化されます。これらは、`+`、`-`、`*`、`/`、`//`、`^`、`inv`、`one`、`isone`、`zero`、`iszero`（`Pol` または `Number` と `Frac{Pol{T}}` の間で操作できる）という算術演算を持っています。

```julia-repl
julia> a=1/(q+1)
Frac{Pol{Int64}}: 1/(q+1)

julia> Pol(2/a) # `Pol` に戻す
Pol{Int64}: 2q+2

julia> numerator(a)
Pol{Int64}: 1

julia> denominator(a)
Pol{Int64}: q+1

julia> m=[q+1 q+2;q-2 q-3]
2×2 Matrix{Pol{Int64}}:
 q+1  q+2
 q-2  q-3

julia> n=inv(Frac.(m)) # 有理数に変換して行列を反転
2×2 Matrix{Frac{Pol{Int64}}}:
 (-q+3)/(2q-1)  (-q-2)/(-2q+1)
 (q-2)/(2q-1)   (q+1)/(-2q+1)

julia> map(x->x(1),n) # 逆行列を1で評価
2×2 Matrix{Float64}:
  2.0   3.0
 -1.0  -2.0

julia> map(x->x(1;Rational=true),n) # //を使用して1で評価
2×2 Matrix{Rational{Int64}}:
  2   3
 -1  -2
```

有理数もブロードキャストのためのスカラーであり、ソートすることができます（`cmp` と `isless` メソッドを持っています）。
