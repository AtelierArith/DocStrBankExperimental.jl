```
ルーツ
```

`f(x) = 0` を解くためのユニバリアント、スカラー関数用のパッケージです。

基本的なメソッドは次の通りです。

  * [`find_zero`](@ref) は、ゼロを特定するためのいくつかのメソッドのいずれかを使用します。
  * [`ZeroProblem`](@ref) は、`CommonSolve` インターフェースを使用してゼロを解決します。
  * [`find_zeros`](@ref) は、指定された区間内のすべてのゼロをヒューリスティックに特定します。

# 拡張ヘルプ

# Julia のルート探索関数

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://JuliaMath.github.io/Roots.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://JuliaMath.github.io/Roots.jl/dev) [![Build Status](https://github.com/JuliaMath/Roots.jl/actions/workflows/ci.yml/badge.svg)](https://github.com/JuliaMath/Roots.jl/actions/workflows/ci.yml) [![codecov](https://codecov.io/gh/JuliaMath/Roots.jl/graph/badge.svg?token=EbswopIDMU)](https://codecov.io/gh/JuliaMath/Roots.jl)

このパッケージは、浮動小数点数学を使用して単一の実変数のスカラー関数のルート、またはゼロを見つけるためのシンプルなルーチンを含んでいます。`find_zero` 関数は主要なインターフェースを提供します。基本的な呼び出しは `find_zero(f, x0, [M], [p]; kws...)` で、通常、`f` は関数、`x0` は開始点またはブレッキング区間、`M` は使用されるデフォルトアルゴリズムを調整するために使用され、`p` はパラメータを渡すために使用されます。

さまざまなアルゴリズムには次のものが含まれます。

  * 二分法のようなアルゴリズム。ブレッキング区間が知られている関数（`f(a)` と `f(b)` が交互の符号を持つもの）では、`Bisection` のようなブレッキングメソッドを指定できます。デフォルトは `Bisection` で、ほとんどの浮動小数点数型に対して、浮動小数点ストレージの規約を利用して使用されます。他の数値型（例：`BigFloat`）では、Alefeld、Potra、および Shi のアルゴリズムがデフォルトで使用されます。これらのデフォルトメソッドは収束が保証されています。他のブレッキングメソッドも利用可能です。
  * 複数の導関数なしのアルゴリズム。これらは、`Order0`、`Order1`（セカント法）、`Order2`（ステッフェンセン法）、`Order5`、`Order8`、および `Order16` を通じて指定されます。数は大まかに収束の順序を示します。`Order0` メソッドはデフォルトであり、最も堅牢ですが、収束するまでにより多くの関数呼び出しが必要になる場合があります。高次のメソッドはより速い収束を約束しますが、必ずしも `Order1` や `Order2` よりも少ない関数呼び出しで結果を得られるわけではありません。`Roots.Order1B` と `Roots.Order2B` メソッドは、ゼロの重複に依存しない超線形および二次収束メソッドです。
  * 導関数を指定する必要がある歴史的なアルゴリズムがあります：`Roots.Newton` と `Roots.Halley`。`Roots.Schroder` は、ニュートン法のような二次法を提供し、ゼロの重複に依存しません。これは `Roots.ThukralXB` によって一般化されます（`X` は 2、3、4、または 5 です）。
  * `Roots.Brent()`、`Roots.LithBoonkkampIJzermanBracket`、および `Roots.LithBoonkkampIJzerman` のような、エクスポートされていないアルゴリズムもいくつかあります。

各メソッドのドキュメントには追加の詳細があります。

いくつかの例：

```jldoctest readme
julia> using Roots

julia> f(x) = exp(x) - x^4;

julia> α₀, α₁, α₂ = -0.8155534188089607, 1.4296118247255556, 8.6131694564414;

julia> find_zero(f, (8,9), Bisection()) ≈ α₂ # ブレッキングが指定された二分法
true

julia> find_zero(f, (-10, 0)) ≈ α₀ # `find_zero(f, x)` の x がスカラーでない場合は二分法がデフォルト
true


julia> find_zero(f, (-10, 0), Roots.A42()) ≈ α₀ # 二分法よりも少ない関数評価
true
```

非ブレッキングメソッドの場合、初期位置はスカラーとして渡されるか、セカント法のようなメソッドの場合は `(x_0, x_1)` のような反復可能なものとして渡されます：

```jldoctest readme
julia> find_zero(f, 3) ≈ α₁  # find_zero(f, x0::Number) は Order0() を使用します
true

julia> find_zero(f, 3, Order1()) ≈ α₁ # 同じ答え、異なるメソッド（セカント）
true

julia> find_zero(f, (3, 2), Order1()) ≈ α₁ # (3, f(3), (2, f(2)) でセカント法を開始
true


julia> find_zero(sin, BigFloat(3.0), Order16()) ≈ π # Order1() を使用して 2 回の反復で 6
true
```

`find_zero` 関数は呼び出し可能なオブジェクトとともに使用できます：

```jldoctest readme
julia> using Polynomials;

julia> x = variable();

julia> find_zero(x^5 - x - 1, 1.0) ≈ 1.1673039782614187
true
```

この関数は `Unitful` パッケージの単位を尊重する必要があります：

```jldoctest readme
julia> using Unitful

julia> s, m  = u"s", u"m";

julia> g, v₀, y₀ = 9.8*m/s^2, 10m/s, 16m;


julia> y(t) = -g*t^2 + v₀*t + y₀
y (generic function with 1 method)

julia> find_zero(y, 1s)  ≈ 1.886053370668014s
true
```

ニュートン法は手動で導関数を取らずに使用できます。以下の例では `ForwardDiff` パッケージを使用します：

```jldoctest readme
julia> using ForwardDiff

julia> D(f) = x -> ForwardDiff.derivative(f,float(x))
D (generic function with 1 method)
```

今、私たちは次のようにします：

```jldoctest readme
julia> f(x) = x^3 - 2x - 5
f (generic function with 1 method)

julia> x0 = 2
2

julia> find_zero((f, D(f)), x0, Roots.Newton()) ≈ 2.0945514815423265
true
```

自動導関数により、関数の臨界点を見つけるための簡単な解決策が可能になります。

```jldoctest readme
julia> using Statistics: mean, median

julia> as = rand(5);

julia> M(x) = sum((x-a)^2 for a in as)
M (generic function with 1 method)

julia> find_zero(D(M), .5) ≈ mean(as)
true

julia> med(x) = sum(abs(x-a) for a in as)
med (generic function with 1 method)

julia> find_zero(D(med), (0, 1)) ≈ median(as)
true
```

### CommonSolve インターフェース

[DifferentialEquations](https://github.com/SciML/DifferentialEquations.jl) インターフェースは、問題を設定し、問題を初期化し、問題を解決するために、`ZeroProblem` 型と `init`、`solve!`、および `solve` メソッド（[CommonSolve](https://github.com/SciML/CommonSolve.jl) から）を使用して実装されています。

たとえば、次のように多くの異なるメソッドで問題を解決できます：

```jldoctest readme
julia> f(x) = exp(-x) - x^3
f (generic function with 1 method)

julia> x0 = 2.0
2.0

julia> fx = ZeroProblem(f, x0)
ZeroProblem{typeof(f), Float64}(f, 2.0)

julia> solve(fx) ≈ 0.7728829591492101
true
```

デフォルトがなく、単一の初期点が指定されている場合、デフォルトの `Order1` メソッドが使用されます。`solve` メソッドは、他のルート解法メソッドを渡すことができ、他のオプションとともに使用できます。たとえば、収束基準を使用して `Order2` メソッドを使用するには（以下を参照）、`|xₙ - xₙ₋₁| ≤ δ` のように呼び出すことができます：

```jldoctest readme
julia> solve(fx, Order2(); atol=0.0, rtol=0.0) ≈ 0.7728829591492101
true
```

`find_zero` が非収束時にエラーを返すのに対し、`solve` は非収束時に `NaN` を返します。

次の例では、ゼロが `0.0` にありますが、ほとんどの初期値では `±∞` に逃げるため、相対許容誤差が誤解を招く値を返すことがあります。ここで違いを確認できます：

```jldoctest readme
julia> f(x) = cbrt(x) * exp(-x^2)
f (generic function with 1 method)

julia> x0 = 0.1147
0.1147

julia> find_zero(f, x0, Roots.Order5()) ≈ 5.936596662527689 # |f(xₙ)| ≤ |xₙ|ϵ で停止
true

julia> find_zero(f, x0, Roots.Order1(), atol=0.0, rtol=0.0) # |f(xn)| のチェックがないためエラー
ERROR: Roots.ConvergenceFailed("アルゴリズムが収束しませんでした")
[...]

julia> fx = ZeroProblem(f, x0);

julia> solve(fx, Roots.Order1(), atol=0.0, rtol=0.0) # NaN、エラーではない
NaN

julia> fx = ZeroProblem((f, D(f)), x0); # 高次メソッドはこの関数のゼロを特定できます

julia> solve(fx, Roots.LithBoonkkampIJzerman(2,1), atol=0.0, rtol=0.0)
0.0
```

関数はパラメータ化することができ、次のように示されています：

```jldoctest readme
julia> f(x, p=2) = cos(x) - x/p
f (generic function with 2 methods)

julia> Z = ZeroProblem(f, pi/4)
ZeroProblem{typeof(f), Float64}(f, 0.7853981633974483)

julia> solve(Z, Order1()) ≈ 1.0298665293222586     # p=2 デフォルトを使用
true

julia> solve(Z, Order1(), p=3) ≈ 1.170120950002626 # p=3 を使用
true

julia> solve(Z, Order1(), 4) ≈ 1.2523532340025887  # 位置によって、p=4 を使用
true
```

### 複数のゼロ

`find_zeros` 関数は、指定された区間内のすべてのゼロを検索するために使用できます。基本的なアルゴリズムは、区間を多くのサブ区間に分割します。各サブ区間について、ブレッキングがある場合はブレッキングアルゴリズムを使用してゼロを特定し、そうでない場合は導関数なしのメソッドを使用してゼロを検索します。このヒューリスティックアルゴリズムは、さまざまな理由でゼロを見逃す可能性があるため、結果は他の手段で確認する必要があります。

```jldoctest readme
julia> f(x) = exp(x) - x^4
f (generic function with 2 methods)

julia> find_zeros(f, -10,10) ≈ [α₀, α₁, α₂] # 上記から
true
```

区間は、`extrema` が定義された構造体を使用して指定することもでき、`extrema` は異なる2つの値を返します：

```jldoctest readme
julia> using IntervalSets

julia> find_zeros(f, -10..10) ≈ [α₀, α₁, α₂]
true
```

（より難しい問題については、[IntervalRootFinding](https://github.com/JuliaIntervals/IntervalRootFinding.jl) パッケージが、`find_zeros` によって返されるヒューリスティックに特定された値ではなく、保証された結果を提供します。）

### 収束

ほとんどのアルゴリズムでは、収束は次の条件で決定されます。

  * 値 `|f(x_n)| <= tol` で、`tol = max(atol, abs(x_n)*rtol)`、または
  * 値 `x_n ≈ x_{n-1}` で、許容誤差 `xatol` と `xrtol` *および* `f(x_n) ≈ 0` で、`atol` と `rtol` に基づく*緩和された*許容誤差。

`find_zero` アルゴリズムは次の条件で停止します。

  * `NaN` または `Inf` に遭遇した場合、または
  * 反復回数が `maxevals` を超えた場合

アルゴリズムが停止し、緩和された収束基準が満たされると、疑わしいゼロが返されます。そうでない場合は、収束しないことを示すエラーがスローされます。許容誤差を調整するために、`find_zero` はキーワード引数 `atol`、`rtol`、`xatol`、および `xrtol` を受け入れます。上記のいくつかの例で見られます。

`Bisection` および `Roots.A42` メソッドは、許容誤差がゼロに設定されていても収束が保証されているため、これらがデフォルトです。低精度が必要な場合に関数呼び出しの数を減らすために、`xatol` および `xrtol` に非ゼロの値を指定できます。

```jldoctest readme
julia> fx = ZeroProblem(sin, (3,4));

julia> solve(fx, Bisection(); xatol=1/16)
3.125
```

## 代替インターフェース

この機能は、MATLAB ユーザーに馴染みのある `fzero` 関数によって提供されます。`Roots` はこの代替インターフェースも提供します。

  * `fzero(f, x0::Real; order=0)` は導関数なしのメソッドを呼び出します。順序は `Order0`、`Order1` などのいずれかを指定します。
  * `fzero(f, a::Real, b::Real)` は `Bisection` メソッドで `find_zero` アルゴリズムを呼び出します。
  * `fzeros(f, a::Real, b::Real)` は `find_zeros` を呼び出します。

### 使用例

```jldoctest readme
julia> f(x) = exp(x) - x^4
f (generic function with 2 methods)

julia> fzero(f, 8, 9) ≈ α₂   # ブレッキング
true

julia> fzero(f, -10, 0) ≈ α₀
true

julia> fzeros(f, -10, 10) ≈ [α₀, α₁, α₂]
true

julia> fzero(f, 3) ≈ α₁      # デフォルトは Order0()
true

julia> fzero(sin, big(3), order=16)  ≈ π # 高次メソッドを使用
true
```
