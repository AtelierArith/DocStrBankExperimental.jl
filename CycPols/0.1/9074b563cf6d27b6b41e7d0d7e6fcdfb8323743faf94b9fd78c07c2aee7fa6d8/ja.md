このパッケージは、円分多項式の積に関するものです。

円分数および有理数またはいくつかの円分体上の円分多項式は、有限還元群およびスぺツェスの理論において重要です。特に、円分ヘッケ代数のシュール要素は円分多項式の積です。

型 `CycPol` は、すべての極またはゼロが0または単位根に等しい1変数の有理数の分数と定数、または多項式との積を表します。`CycPol` としてそのようなオブジェクトを表現する利点は、見栄えが良い（因数分解された形）、ストレージが少ない、高速な乗算、除算、および評価です。欠点は、加算と減算が実装されていないことです！

このパッケージは、`LaurentPolynomials` パッケージによって定義された多項式 `Pol` と、`CyclotomicNumbers` パッケージによって定義された円分数 `Cyc` を使用します。

メソッド `CycPol(a::Pol)` は、`a` を最大の円分多項式で割ることによって `CycPol` に変換し、多項式のいくつかの根が単位根でない場合は `Pol` の `coefficient` を残します。

```julia-repl
julia> using LaurentPolynomials

julia> @Pol q
Pol{Int64}: q

julia> p=CycPol(q^25-q^24-2q^23-q^2+q+2) # `Pol` の係数が残る
(q-2)Φ₁Φ₂Φ₂₃

julia> p(q) # q で CycPol p を評価
Pol{Int64}: q²⁵-q²⁴-2q²³-q²+q+2

julia> p*inv(CycPol(q^2+q+1)) # `*`, `inv`, `/` および `//` が定義されている
(q-2)Φ₁Φ₂Φ₃⁻¹Φ₂₃

julia> -p  # スカラーで乗算できる
(-q+2)Φ₁Φ₂Φ₂₃

julia> valuation(p)
0

julia> degree(p)
25

julia> lcm(p,CycPol(q^3-1)) # CycPol 間の lcm は高速
(q-2)Φ₁Φ₂Φ₃Φ₂₃
```

```julia-rep1
julia> print(p)
CycPol(Pol([-2, 1]),0,(1,0),(2,0),(23,0)) # Julia で読み取れる形式
```

`CycPol` をいくつかの `Pol` 値で評価すると、一般的には `Pol` が得られます。`Pol()^n`（すなわち `q^n`）または `Pol([E(n,k)],1)`（すなわち `qζₙᵏ`）で評価する場合には、`CycPol` のまま値を保持できる例外があります。その場合、`subs` がその評価を返します：

```julia-repl
julia> subs(p,Pol()^-1) # q⁻¹ で CycPol として評価
(2-q⁻¹)q⁻²⁴Φ₁Φ₂Φ₂₃

julia> using CyclotomicNumbers

julia> subs(p,Pol([E(2)],1)) # または -q で
(-q-2)Φ₁Φ₂Φ₄₆
```

`CycPol` を印刷する際に使用される変数名は `Pol` の場合と同じです。

`CycPol` を表示する際、円分多項式 `Φₙ` の拡張体上のいくつかの因子には特別な名前が付けられます。もし `n` に原始根 `ξ` がある場合、`ϕ′ₙ` は `ζ` が `ξ` の奇数乗を走る `(q-ζ)` の積であり、`ϕ″ₙ` は偶数乗の積です。小さな `n` に対してはさらにいくつかの因子が認識されます。

```julia-repl
julia> CycPol(q^6-E(4))
Φ″₈Φ⁽¹³⁾₂₄
```

関数 `show_factors` は、与えられた `n` に対する認識された因子の完全なリストを提供します：

```julia-repl
julia> CycPols.show_factors(24)
15-element Vector{Tuple{CycPol{Int64}, Pol}}:
 (Φ₂₄, q⁸-q⁴+1)
 (Φ′₂₄, q⁴+ζ₃²)
 (Φ″₂₄, q⁴+ζ₃)
 (Φ‴₂₄, q⁴-√2q³+q²-√2q+1)
 (Φ⁗₂₄, q⁴+√2q³+q²+√2q+1)
 (Φ⁽⁵⁾₂₄, q⁴-√6q³+3q²-√6q+1)
 (Φ⁽⁶⁾₂₄, q⁴+√6q³+3q²+√6q+1)
 (Φ⁽⁷⁾₂₄, q⁴+√-2q³-q²-√-2q+1)
 (Φ⁽⁸⁾₂₄, q⁴-√-2q³-q²+√-2q+1)
 (Φ⁽⁹⁾₂₄, q²+ζ₃²√-2q-ζ₃)
 (Φ⁽¹⁰⁾₂₄, q²-ζ₃²√-2q-ζ₃)
 (Φ⁽¹¹⁾₂₄, q²+ζ₃√-2q-ζ₃²)
 (Φ⁽¹²⁾₂₄, q²-ζ₃√-2q-ζ₃²)
 (Φ⁽¹³⁾₂₄, q⁴-ζ₄q²-1)
 (Φ⁽¹⁴⁾₂₄, q⁴+ζ₄q²-1)
```

そのような因子は次のように直接取得できます：

```julia-repl
julia> CycPol(;conductor=24,no=7)
Φ⁽⁷⁾₂₄

julia> CycPol(;conductor=24,no=7)(q)
Pol{Cyc{Int64}}: q⁴+√-2q³-q²-√-2q+1
```

このパッケージはまた、関数 `cylotomic_polynomial` を定義します：

```julia-repl
julia> p=cyclotomic_polynomial(24)
Pol{Int64}: q⁸-q⁴+1

julia> CycPol(p) # CycPol(;conductor=24,no=0) と同じ
Φ₂₄
```
