このパッケージは、Puiseux多項式を実装しています。これは、変数 `xᵢ` のモノミアル `x₁^{a₁}… xₙ^{aₙ}` のいくつかの型 `C` の係数を持つ線形結合です。ここで、`aᵢ` は任意の有理数であり、`xᵢ` は変数です。`aᵢ` が整数の場合は「多変数ローレン多項式」と呼び、`aᵢ` が正の整数の場合は「多変数多項式」（または真の多項式）と呼びます。

このパッケージはまた、多変数有理数分数を実装しており、これは2つのローレン多項式の商として構成され（これは2つの真の多項式の商に正規化されます）、特にこのパッケージは多変数多項式と多変数有理数分数の実装として非常に使いやすく（そしておそらくかなり良い）です。

Puiseux多項式の主な用途は、`C` の要素が代数的閉体を形成する場合、それらが多変数有理数分数の代数的閉包の整数環であることです。特に、サイコトミック・ヘッケ代数は、そこにおけるキャラクタ値と表現を取ります。

このパッケージは、`Reexport`、`LaurentPolynomials`、および `ModuleElts` のパッケージのみに依存しています。`LaurentPolynomials` によって定義された名前は、このパッケージによって再エクスポートされます。

私たちのPuiseux多項式は、パラメトリック型 `Mvp{C,E}` を持ち、ここで `C` は係数の型、`E` は指数の型です：ローレン多項式の場合は `E=Int`、より一般的なPuiseux多項式の場合は `E=Rational{Int}` です。`Mvp` の型を印刷する際、`E==Int` の場合は `C` のみが印刷されます。有理数分数は、分子と分母が真の多項式である場合にのみ定義されます；それらは型 `Frac{Mvp{C,Int}}` を持ちます。2つのローレン多項式の商は、2つの真の多項式の商に正規化されます。

まず、Puiseux多項式を作成する方法を見てみましょう。

`@Mvp x₁,…,xₙ`

は、各Julia名 `xᵢ` に多変数多項式または有理数分数を構築するのに適した不定元を表す `Mvp` を割り当てます。`Mvp(:x₁)` は、変数 `x₁` に割り当てることなく同じ `Mvp` を作成します。

```julia-repl
julia> @Mvp x,y # 変数 x,y を作成

julia> (x+y^-1)^3
Mvp{Int64}: x³+3x²y⁻¹+3xy⁻²+y⁻³

julia> x+Mvp(:z)
Mvp{Int64}: x+z

julia> x^(1//2)  # Puiseuxモノミアル
Mvp{Int64,Rational{Int64}}: x½

julia> Mvp(3)  # 定数項のみのMvpに数を変換
Mvp{Int64}: 3
```

上記のように、変数を使用して `Mvp` を作成するのが便利です。関数 `repr` または `print` は、Juliaで読み戻すことができる形式で `Mvp` を表示します – これは、repl、IJulia、またはpluto以外のコンテキストで `Mvp` が印刷される方法でもあります：

```julia-repl
julia> repr(3x*y^-2+4)
"Mvp{Int64, Int64}([:x=>1,:y=>-2]=>3,[]=>4)"
```

この形式をカジュアルに使用しない方が良いです。なぜなら、引数は*必ず*正規化されている必要があるからです（キーでソートされ、重複キーがない）。

モノミアルと1項の `Mvp` のみが非整数の冪に上げることができます；1項の定数 `c` とモノミアル `m` の積である `Mvp` は、`root(c,d)` が定義されている場合に限り、分母 `d` の分数冪に上げることができます（これは浮動小数点数の場合の `c^{1//d}` に相当します）；

```julia-repl
julia> (4x)^(1//2)
Mvp{Int64,Rational{Int64}}: 2x½

julia> (2.0x)^(1//2)
Mvp{Float64,Rational{Int64}}: 1.4142135623730951x½

julia> root(2.0x)
Mvp{Float64,Rational{Int64}}: 1.4142135623730951x½
```

`root` を異なる方法で定義したい場合もあります。たとえば、私の別のパッケージ `CylotomicNumbers` では、有理数の平方根をサイコトミックとして定義し、また、単位根の任意の根を実装しています。

```julia-rep1
julia> using CyclotomicNumbers

julia> (2x)^(1//2)
Mvp{Cyc{Int64},Rational{Int64}}: √2x½

julia> (E(3)*x)^(2//3)
Mvp{Cyc{Int64},Rational{Int64}}: ζ₉²x⅔
```

`Mvp` を分解する方法はいくつかあります。以下は最も直接的な方法です；また、関数 `coefficient`、`coefficients`、`pairs`、`monomials`、`variables`、`powers` も参照してください。

```julia-repl
julia> p=3x*y^-2+4
Mvp{Int64}: 3xy⁻²+4

julia> term(p,1) # 項は Pair モノミアル=>係数
xy⁻² => 3

julia> term(p,2) # 自明なモノミアル Monomial() は空文字列として印刷される
 => 4

julia> length(p) # 項の数
2

julia> term.(p,1:length(p)) # pairs(p) と同じ
2-element Vector{Pair{Monomial{Int64}, Int64}}:
 xy⁻² => 3
      => 4

julia> last(term(p,1)) # first(coefficients(p)) と同じ
3

julia> m=first(term(p,1)) # first(monomials(p)) と同じ
Monomial{Int64}:xy⁻²

julia> length(m) # m の変数の数
2

julia> map((x,y)->x=>y,variables(m),powers(m)) # pairs(m) と同じ
2-element Vector{Pair{Symbol, Int64}}:
 :x => 1
 :y => -2

julia> degree(m,:x) # m における x の冪
1

julia> degree(m,:y) # m における y の冪
-2
```

`Mvp` の評価と次数は、全体的または変数ごとに調べることができます。

```julia-repl
julia> p
Mvp{Int64}: 3xy⁻²+4

julia> variables(p)
2-element Vector{Symbol}:
 :x
 :y

julia> degree(p),degree(p,:x),degree(p,:y)
(0, 1, 0)

julia> valuation(p),valuation(p,:x),valuation(p,:y)
(-1, 0, -2)
```

`Mvp` の項はモノミアル順序によって順序付けられています（つまり、モノミアルに対する全順序で、`x<y` があれば、任意のモノミアル `x,y,z` に対して `xz<yz` が成り立ちます）。項は降順に並んでおり、最初の項が最も高いものです。デフォルトの順序は `lex` です。`grlex` および `grevlex` の順序も実装されています（それらのドキュメントと `grobner_basis` を参照して使用方法を確認してください）。

`Mvp` は、評価と次数が `0` の場合に*スカラー*です（それは `one` モノミアルに対応する単一の項を持ちます）。関数 `scalar` は、`Mvp` がスカラーである場合は定数係数を返し、そうでない場合は `nothing` を返します。

通常の算術（`+`、`-`、`*`、`^`、`/`、`//`、`one`、`isone`、`zero`、`iszero`、`==`）が機能します。型 `<:Number` の要素は、係数のスカラー乗算または除算のためにスカラーと見なされます。

```julia-repl
julia> p
Mvp{Int64}: 3xy⁻²+4

julia> p^2
Mvp{Int64}: 9x²y⁻⁴+24xy⁻²+16

julia> p/2
Mvp{Float64}: 1.5xy⁻²+2.0

julia> p//2
Mvp{Rational{Int64}}: (3//2)xy⁻²+2//1
```

`Mvp` を別の型の `Mvp` に変換する場合、2つの型パラメータ（係数の型と指数の型）を指定する必要があります。

```julia-repl
julia> Mvp{Float64,Rational{Int}}(p)
Mvp{Float64,Rational{Int64}}: 3.0xy⁻²+4.0
```

`Mvp` を評価し、いくつかの変数の値を設定するには、関数呼び出し構文を使用します。

```julia-repl
julia> p=x+y
Mvp{Int64}: x+y

julia> p(x=2)    # x=2 で p を評価
Mvp{Int64}: y+2

julia> value(p,:x=>2) # より明示的な `value` 関数もあります。
Mvp{Int64}: y+2

julia> p(x=2,y=x) # 同時評価
Mvp{Int64}: x+2

julia> value(p,:x=>2,:y=>x)
Mvp{Int64}: x+2
```

`Mvp` は常に `Mvp` に評価されることに注意してください、一貫性のためです。`Mvp` のすべての変数に値を与えた結果に `scalar` を使用して数値を取得する必要があります。

```julia-repl
julia> p(x=1,y=2)
Mvp{Int64}: 3

julia> scalar(p(x=1,y=2))
3

julia> v=(x^(1//2))(x=2.0)
Mvp{Float64,Rational{Int64}}: 1.4142135623730951

julia> scalar(v)
1.4142135623730951
```

他の `Mvp` で `Mvp` を割ることができるのは、割り算が正確な場合のみで、2つの `Mvp` の `gcd` と `lcm` を計算できます。

```julia-repl
julia> LinearAlgebra.exactdiv(x^2-y^2,x-y) # 割り算が正確でない場合はエラー
Mvp{Int64}: x+y

julia> (x+y)/(2x^2)   # モノミアルで割る
Mvp{Float64}: 0.5x⁻¹+0.5x⁻²y

julia> (x+y)//(2x^2)
Mvp{Rational{Int64}}: (1//2)x⁻¹+(1//2)x⁻²y

julia> (x+y)/(x-y)   # 割り算が正確でない場合は有理数分数が得られる
Frac{Mvp{Int64, Int64}}: (x+y)/(x-y)
```

非モノミアルローレン多項式を負の冪に上げると、有理数分数が返されます。有理数分数は、分子と分母が互いに素な真の多項式であるように正規化されます。これらは、`+`、`-`、`*`、`/`、`//`、`^`、`inv`、`one`、`isone`、`zero`、`iszero`（これらの操作は `Mvp` または `Number` と `Frac{<:Mvp}` の間で機能します）を持ちます。

```julia-repl
julia> (x+1)^-2
Frac{Mvp{Int64, Int64}}: 1/(x²+2x+1)

julia> x+1/(y+1)
Frac{Mvp{Int64, Int64}}: (xy+x+1)/(y+1)

julia> 1/(y-1)-1/(y+1)
Frac{Mvp{Int64, Int64}}: 2/(y²-1)
```

`Frac` を評価し、いくつかの変数の値を設定するには、関数呼び出し構文または `value` 関数を使用します：

```julia-repl
julia> ((x+y)/(x-y))(x=y+1)
Mvp{Float64}: 2.0y+1.0

julia> value((x+y)/(x-y),:x=>y+1;Rational=true) # Rational=true は // を使用することを示します
Mvp{Int64}: 2y+1
```

`Frac` は `numerator` と `denominator` を使用して分解できます。`Frac` と `Mvp` はブロードキャスティングのスカラーであり、ソート可能です（`cmp` と `isless` メソッドを持ちます）。

```julia-repl
julia> m=[x+y x-y;x+1 y+1]
2×2 Matrix{Mvp{Int64, Int64}}:
 x+y  x-y
 x+1  y+1

julia> n=inv(Frac.(m))
2×2 Matrix{Frac{Mvp{Int64, Int64}}}:
 (-y-1)/(x²-2xy-y²-2y)  (x-y)/(x²-2xy-y²-2y)
 (x+1)/(x²-2xy-y²-2y)   (-x-y)/(x²-2xy-y²-2y)

julia> lcm(denominator.(n))
Mvp{Int64}: x²-2xy-y²-2y
```

最後に、`Mvp` には係数に作用する `conj`、`adjoint` メソッド、導関数メソッド、`positive_part`、`negative_part`、および `bar` メソッド（カズダン・ルスティグ理論に便利）があります。

```julia_repl
julia> @Mvp z
Mvp{Int64}: z

julia> hessian(p,vars)=[derivative(derivative(p,x),y) for x in vars, y in vars]
hessian (generic function with 1 method)

julia> hessian(x^2*y^2*z^2,[:x,:y,:z])
3×3 Matrix{Mvp{Int64, Int64}}:
 2y²z²  4xyz²  4xy²z
 4xyz²  2x²z²  4x²yz
 4xy²z  4x²yz  2x²y²

julia> jacobian(pols,vars)=[derivative(p,v) for p in pols, v in vars]
jacobian (generic function with 1 method)

julia> jacobian([x,y,z],[:x,:y,:z])
3×3 Matrix{Mvp{Int64, Int64}}:
 1  0  0
 0  1  0
 0  0  1

julia> p=(x+y^-1)^4
Mvp{Int64}: x⁴+4x³y⁻¹+6x²y⁻²+4xy⁻³+y⁻⁴

julia> positive_part(p)
Mvp{Int64}: x⁴

julia> negative_part(p)
Mvp{Int64}: y⁻⁴

julia> bar(p)
Mvp{Int64}: y⁴+4x⁻¹y³+6x⁻²y²+4x⁻³y+x⁻⁴
```

私たちの多項式の一般性の度合いにもかかわらず、速度はあまり悪くありません。Fatemanテスト f(f+1) の場合、ここで f=(1+x+y+z+t)^15 で、3秒かかります。Nemoの論文によると、Sagemathは10秒、Nemoは1.6秒かかります。
