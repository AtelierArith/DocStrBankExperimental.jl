```
SolveTwoStageRO_CCG(args...; kwargs...)
```

次の二段階ロバスト最適化問題を（ネストされた）カラム・アンド・制約生成（C&CG）法を使用して解決します（`Ref.1-2`）：

```formulation
Min_y c' * y + Max_{u ∈ U} Min_{x ∈ F(y, u)} b' * x

Subject to:

    A * y ≥ d, y ∈ Sy

    F(y, u) = {x ∈ Sx: G * x ≥ h - E * y - M * u}

    Uは不確実性集合です
```

ここで、`Sy`と`Sx`は非負の実数空間または非負の混合整数空間であることが許可されています。

P.S. 次の穏やかな仮定が成り立つことを期待しています（`Ref.1-2`）：

  * `Sx`が非負の実数空間であるときの相対的完全回収の仮定、すなわち、与えられた`y`と`u`に対して第二段階の意思決定問題（線形プログラム）は常に実行可能です。
  * `Sx`が非負の混合整数空間であるとき、少なくとも1つの実数次元を持つこと、すなわち、混合整数プログラミングの回収問題には少なくとも1つの連続回収変数があります。
  * `Sx`が非負の混合整数空間であるときの拡張相対的完全回収特性、すなわち、`y`、`u`、および`x`の整数部分を固定することによって得られる問題（線形プログラム）は常に実行可能で有界です。
  * `Sx`が非負の混合整数空間であるとき、離散回収変数（すなわち、`x`の整数部分）の実行可能集合は有界です。

# 引数

  * `c::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`c`は最初にベクトル形式に変換する必要があります。例：`c = [2]`。
  * `b::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`b`は最初にベクトル形式に変換する必要があります。例：`b = [1]`。
  * `A::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`A`は最初に行列形式に変換する必要があります。例：`A = [1 2]`、`A = [1; 2;;]`または`A = [0;;]`。
  * `d::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`d`は最初にベクトル形式に変換する必要があります。例：`d = [0]`。
  * `G::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`G`は最初に行列形式に変換する必要があります。例：`G = [1 2]`、`G = [1; 2;;]`または`G = [1;;]`。
  * `h::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`h`は最初にベクトル形式に変換する必要があります。例：`h = [0]`。
  * `E::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`E`は最初に行列形式に変換する必要があります。例：`E = [1 2]`、`E = [1; 2;;]`または`E = [-1;;]`。
  * `M::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`M`は最初に行列形式に変換する必要があります。例：`M = [1 2]`、`M = [1; 2;;]`または`M = [-1;;]`。
  * `Sy::Vector{<:BasicDomain}`: 非負の実数空間または非負の混合整数空間であることが許可されています。次の3つの基本データ型のインスタンス（の混合）からなるベクトルとして構築する必要があります：`Rplus`、`ZeroOne`および`Zplus`。例：`Sy = [ZeroOne()]`は1次元のバイナリ空間`{0, 1}`を示し、`Sy = [Rplus(2), Zplus(3)]`は5次元の非負の混合整数空間`ℝ₊² × ℤ₊³`を示します。後者は`Sy = [fill(Rplus(), 2), fill(Zplus(), 3)]`と同等です。
  * `Sx::Vector{<:BasicDomain}`: 非負の実数空間または非負の混合整数空間であることが許可されています。前者の場合、`Ref.1`からのアルゴリズム（C&CG）が呼び出されます。後者の場合、`Ref.2`からのアルゴリズム（ネストされたC&CG）が呼び出されます。次の3つの基本データ型のインスタンス（の混合）からなるベクトルとして構築する必要があります：`Rplus`、`ZeroOne`および`Zplus`。構築方法は`Sy`と同じです。
  * `U::Union{Model, Polyhedron}`: 不確実性集合は、`JuMP.jl`パッケージを使用して`Model`として構築するか、`Polyhedra.jl`パッケージを使用して`Polyhedron`として構築することが許可されています。このパッケージは、ユーザーが上記のパッケージを追加で`using/import`することなく、不確実性集合を便利にモデル化できるようにするために、`JuMP.jl`、`Polyhedra.jl`およびその他の関連パッケージからのいくつかの必要な関数を統合しています。簡単な使用法については`Examples`セクションを参照してください。`JuMP`モデルの不確実性集合で`u`として登録された名前の変数のみが不確実性変数として認識されることに注意してください。ただし、登録された変数名が1つだけの場合（またはすべての変数が匿名の場合）を除きます。

# キーワード

  * `MPsolver::Module = HiGHS`: マスタープログラム（`MP`）のソルバーです。`Sy`と`Sx`のタイプに基づいて選択する必要があります。一般的に、`Sy`または`Sx`が混合整数空間である場合、混合整数線形プログラム（MILP）をサポートするソルバーである必要があります。
  * `SP1solver::Module = HiGHS`: KKT条件に基づく再定式化（Bi/Tri-Equivalent I）形式のサブ問題のソルバーです（`SP1`）。`SP1`はビッグM法に基づく線形化された再定式化であるため、`U`が単に多面体の不確実性集合である場合、そのソルバーは少なくともMILPソルバーである必要があります。
  * `SP2solver::Module = Ipopt`: このキーワード引数は、`Sx`が非負の実数空間である場合にのみ利用可能です。強双対性に基づく再定式化形式（`SP2`）のサブ問題のソルバーです。この関数は常に最初に`SP1`を解決しようとし、失敗した場合は`SP2`に進みます。`SP2`は、`U`が多面体である場合、少なくともバイリニア最適化問題であるため、これに特化したソルバー、またはおおよそ非凸二次プログラム（QP）をサポートするソルバーが必要です。
  * `SP2solver_max_iter::Integer = 10000`: このキーワード引数は、`Sx`が非負の実数空間である場合にのみ利用可能です。`SP2solver`が`SP2`を解決するための最大反復制限です。
  * `SP2_MPsolver::Module = Ipopt`: このキーワード引数は、`Sx`が非負の混合整数空間である場合にのみ利用可能です。強双対性に基づく再定式化（Bi/Tri-Equivalent II）形式のサブ問題のマスタープログラムのソルバーです（`SP2`）。この関数は常に最初に`SP1`を解決しようとし、失敗した場合は`SP2`に進みます。`SP2`のマスタープログラムには、`U`が単に多面体の不確実性集合である場合でも二次制約が含まれているため、二次制約付き二次プログラム（QCQP）をサポートする効率的なソルバーが必要です。
  * `SP2_MPsolver_max_iter::Integer = 10000`: このキーワード引数は、`Sx`が非負の混合整数空間である場合にのみ利用可能です。`SP2`のマスタープログラムを解決するための最大反復制限です。
  * `SP2_SPsolver::Module = HiGHS`: このキーワード引数は、`Sx`が非負の混合整数空間である場合にのみ利用可能です。強双対性に基づく再定式化（Bi/Tri-Equivalent II）形式のサブ問題のサブ問題のソルバーです（`SP2`）。この関数は常に最初に`SP1`を解決しようとし、失敗した場合は`SP2`に進みます。`SP2`のサブ問題のソルバーは`Sx`のタイプのみに依存するため、`Sx`の混合整数特性のためにMILPソルバーである必要があります。
  * `ϵ::Real = 1e-5`: （ネストされた）C&CG法の全体的な絶対停止基準です。内部の二次プログラミングソルバーがアクティブな場合、それの許容誤差でもあります。
  * `BigM::Real = 1e5`: ビッグM法に基づく線形化された再定式化における`SP1`のビッグM値です。ビッグMに対して厳密な上限が解析的に得られる場合、アルゴリズムのパフォーマンスが向上することに注意してください。
  * `verbose::Bool = true`: 解決プロセスの詳細な出力を制御するスイッチです。

# 戻り値

この関数は、次の順序でエントリを持つ`Tuple{Vector{Real}, Real, Integer}`を返します：

  * `y::Vector{Real}`: 第一段階の意思決定変数`y`の最適解。
  * `objv::Real`: 二段階ロバスト最適化問題の最適目的値。
  * `k::Integer`: 解決プロセスが終了する際の総反復回数。

# 例

```julia
using MKLTwoStageRO
```

### ケース-1:

```julia
c = [2]; b = [1];
A = [0;;]; d = [0]; 
G = [1;;]; h = [0]; E = [-1;;]; M = [-1;;];
Sy = [ZeroOne()]; Sx = [Rplus()]; 
# JuMP `Model`型の不確実性集合で関数を呼び出す：
UncMod = Model()
@variable(UncMod, 0 <= δ <= 1)
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncMod) 
# `Polyhedron`型の不確実性集合で関数を呼び出す：
UncSet = polyhedron(HalfSpace([1], 1) ∩ HalfSpace([-1], 0))
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
```

### ケース-2:

```julia
c = [1, 2]; b = [3];
A = [4 5]; d = [6]; 
G = [1;;]; h = [2]; E = [-3 -4]; M = [-5 -6];
Sx = [Rplus()]; Sy = [Rplus(), ZeroOne()];
# JuMP `Model`型の不確実性集合で関数を呼び出す：
UncMod = Model()
u0 = [0, 0]
@variable(UncMod, u[1:2])
@variable(UncMod, -1 <= δ[1:2] <= 1)
@constraint(UncMod, u == u0 + δ)
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncMod)
# `Polyhedron`型の不確実性集合で関数を呼び出す：
UncSet = polyhedron(UncMod, CDDLib.Library(:exact))
ind_δ = ind_of_var(UncMod, "δ")
UncSet = eliminate(UncSet, ind_δ)
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
```

### ケース-3:

```julia
c = [1]; b = [2; 3];
A = [4;;]; d = [5];
G = [6 7]; h = [8]; E = [10;;]; M = [9;;];
Sy = [Rplus()]; Sx = [Rplus(); ZeroOne()];
# JuMP `Model`型の不確実性集合で関数を呼び出す：
UncMod = Model()
@variable(UncMod, u)
δ = @expression(UncMod, 2u - 1)
@constraint(UncMod, -1 <= δ <= 1)
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncMod)
# `Polyhedron`型の不確実性集合で関数を呼び出す：
UncSet = polyhedron(convexhull([0], [1]))
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
```

# 参考文献

1. Zeng, B., & Zhao, L. (2013). Solving two-stage robust optimization problems using a column-and-constraint generation method. Operations Research Letters, 41(5), 457-461.
2. Zhao, L., & Zeng, B. (2012). An exact algorithm for two-stage robust optimization with mixed integer recourse problems. submitted, available on Optimization-Online. org.

```
