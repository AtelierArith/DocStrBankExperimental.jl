```
SolveTwoStageRO_BDCP(args...; kwargs...)
```

次の二段階ロバスト最適化問題をBenders-dualカッティングプレーン（BDCP）法を使用して解きます（`Ref.1`を参照）：

```formulation
Min_y c' * y + Max_{u ∈ U} Min_{x ∈ F(y, u)} b' * x

制約条件：

    A * y ≥ d, y ∈ Sy

    F(y, u) = {x ∈ Sx: G * x ≥ h - E * y - M * u}

    Uは不確実性集合です
```

ここで、`Sy`は非負の実数空間または非負の混合整数空間であることが許可され、`Sx`は非負の実数空間であることが許可されます。

P.S. 相対的完全回収の仮定が成り立つことを期待しています。すなわち、第二段階の意思決定問題（線形プログラム）は、与えられた`y`と`u`に対して常に実行可能です。（`Ref.1`）

# 引数

  * `c::AbstractVector{<:Real}`: ベクトルである必要があります。退化したスカラー`c`は、最初にベクトル形式に変換する必要があります。例：`c = [2]`。
  * `b::AbstractVector{<:Real}`: ベクトルである必要があります。退化したスカラー`b`は、最初にベクトル形式に変換する必要があります。例：`b = [1]`。
  * `A::AbstractMatrix{<:Real}`: 行列である必要があります。退化したベクトルまたはスカラー`A`は、最初に行列形式に変換する必要があります。例：`A = [1 2]`、`A = [1; 2;;]`または`A = [0;;]`。
  * `d::AbstractVector{<:Real}`: ベクトルである必要があります。退化したスカラー`d`は、最初にベクトル形式に変換する必要があります。例：`d = [0]`。
  * `G::AbstractMatrix{<:Real}`: 行列である必要があります。退化したベクトルまたはスカラー`G`は、最初に行列形式に変換する必要があります。例：`G = [1 2]`、`G = [1; 2;;]`または`G = [1;;]`。
  * `h::AbstractVector{<:Real}`: ベクトルである必要があります。退化したスカラー`h`は、最初にベクトル形式に変換する必要があります。例：`h = [0]`。
  * `E::AbstractMatrix{<:Real}`: 行列である必要があります。退化したベクトルまたはスカラー`E`は、最初に行列形式に変換する必要があります。例：`E = [1 2]`、`E = [1; 2;;]`または`E = [-1;;]`。
  * `M::AbstractMatrix{<:Real}`: 行列である必要があります。退化したベクトルまたはスカラー`M`は、最初に行列形式に変換する必要があります。例：`M = [1 2]`、`M = [1; 2;;]`または`M = [-1;;]`。
  * `Sy::Vector{<:BasicDomain}`: 非負の実数空間または非負の混合整数空間であることが許可されます。次の3つの基本データ型のインスタンス（の混合）からなるベクトルとして構築する必要があります：`Rplus`、`ZeroOne`および`Zplus`。例：`Sy = [ZeroOne()]`は1次元のバイナリ空間`{0, 1}`を示し、`Sy = [Rplus(2), Zplus(3)]`は5次元の非負の混合整数空間`ℝ₊² × ℤ₊³`を示します。後者は`Sy = [fill(Rplus(), 2), fill(Zplus(), 3)]`と同等であることに注意してください。
  * `Sx::Vector{Rplus}`: 基本データ型`Rplus`のインスタンスからなるベクトルとして構築された非負の実数空間である必要があります。例：`Sx = [Rplus(3)]`または同等に`Sx = fill(Rplus(), 3)`。
  * `U::Union{Model, Polyhedron}`: 不確実性集合は、`JuMP.jl`パッケージを使用して`Model`として構築するか、`Polyhedra.jl`パッケージを使用して`Polyhedron`として構築することが許可されます。このパッケージは、`JuMP.jl`、`Polyhedra.jl`およびその他の関連パッケージからのいくつかの必要な関数を統合しており、ユーザーが上記のパッケージを追加で`using/import`することなく不確実性集合を便利にモデル化できるようにします。簡単な使用法については`Examples`セクションを参照してください。`JuMP`モデルの不確実性集合で`u`として登録された名前の変数のみが不確実性変数として認識されることに注意してください。ただし、登録された変数名が1つだけの場合（またはすべての変数が匿名の場合）を除きます。

# キーワード

  * `MPsolver::Module = HiGHS`: マスタープログラム（`MP`）のソルバーです。`Sy`のタイプに基づいて選択する必要があります。一般的に、`Sy`が混合整数空間である場合、混合整数線形プログラム（MILP）をサポートするソルバーである必要があります。
  * `SP1solver::Module = HiGHS`: KKT条件に基づく再定式化（Bi/Tri-Equivalent I）形式のサブプロブレムのソルバーです。`SP1`はビッグM法に基づく線形化された再定式化であるため、`U`が単に多面体の不確実性集合である場合、そのソルバーは少なくともMILPソルバーである必要があります。
  * `SP2solver::Module = Ipopt`: 強双対性に基づく再定式化形式（`SP2`）のサブプロブレムのソルバーです。この関数は常に最初に`SP1`を解こうとし、失敗した場合は`SP2`に進みます。`SP2`は、`U`が多面体である場合、少なくともバイリニア最適化問題であるため、これに特化したソルバー、またはおおよそ非凸二次プログラム（QP）をサポートするソルバーが必要です。
  * `SP2solver_max_iter::Integer = 10000`: `SP2solver`が`SP2`を解くための最大反復制限です。
  * `ϵ::Real = 1e-5`: （ネストされた）C&CG法の全体的な絶対停止基準です。内部の二次プログラミングソルバーがアクティブな場合、それの許容誤差でもあります。
  * `BigM::Real = 1e5`: `SP1`のビッグM法に基づく線形化された再定式化のビッグM値です。ビッグMに対して厳密な上限が分析的に得られる場合、アルゴリズムのパフォーマンスが向上することに注意してください。
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
y, objv = SolveTwoStageRO_BDCP(c, b, A, d, G, h, E, M, Sy, Sx, UncMod) 
# `Polyhedron`型の不確実性集合で関数を呼び出す：
UncSet = polyhedron(HalfSpace([1], 1) ∩ HalfSpace([-1], 0))
y, objv = SolveTwoStageRO_BDCP(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
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
y, objv = SolveTwoStageRO_BDCP(c, b, A, d, G, h, E, M, Sy, Sx, UncMod)
# `Polyhedron`型の不確実性集合で関数を呼び出す：
UncSet = polyhedron(UncMod, CDDLib.Library(:exact))
ind_δ = ind_of_var(UncMod, "δ")
UncSet = eliminate(UncSet, ind_δ)
y, objv = SolveTwoStageRO_BDCP(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
```

# 参考文献

1. Zeng, B., & Zhao, L. (2013). Solving two-stage robust optimization problems using a column-and-constraint generation method. Operations Research Letters, 41(5), 457-461.

```
