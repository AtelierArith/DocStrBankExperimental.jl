```
SolveTwoStageRO_ECCG(args...; kwargs...)
```

次の二段階ロバスト最適化問題を拡張列および制約生成（ECCG）法を使用して解きます（`Ref.1`）：

```formulation
Min_x a' * x + Max_{u ∈ U} Min_{y ∈ Y(x, u)} b' * y

Subject to:

    E * x ≥ e, x ∈ Sx

    Y(x, u) = {y ∈ Sy: A * x + B * y + C * u ≥ c}

    Uは不確実性集合です
```

ここで、`Sx`は非負の実数空間または非負の混合整数空間であることが許可され、`Sy`は非負の実数空間であることが許可されます。

P.S. 我々は実行可能性の仮定が成り立つことを期待しています。すなわち、任意の`u ∈ U`に対して集合`Y(x, u) ≠ ∅`となるような`x ∈ {x ∈ Sx: E * x ≥ e}`が**存在**しますが、相対的完全回収の仮定（すなわち、任意の`x ∈ {x ∈ Sx: E * x ≥ e}`および任意の`u ∈ U`に対して集合`Y(x, u) ≠ ∅`）は必ずしも成り立たないことがあります。(`Ref.1`)

# 引数

  * `a::AbstractVector{<:Real}`: ベクトルである必要があります。退化したスカラー`a`は、最初にベクトル形式に変換する必要があります。例：`a = [2]`。
  * `b::AbstractVector{<:Real}`: ベクトルである必要があります。退化したスカラー`b`は、最初にベクトル形式に変換する必要があります。例：`b = [1]`。
  * `E::AbstractMatrix{<:Real}`: 行列である必要があります。退化したベクトルまたはスカラー`E`は、最初に行列形式に変換する必要があります。例：`E = [1 2]`、`E = [1; 2;;]`または`E = [0;;]`。
  * `e::AbstractVector{<:Real}`: ベクトルである必要があります。退化したスカラー`e`は、最初にベクトル形式に変換する必要があります。例：`e = [0]`。
  * `B::AbstractMatrix{<:Real}`: 行列である必要があります。退化したベクトルまたはスカラー`B`は、最初に行列形式に変換する必要があります。例：`B = [1 2]`、`B = [1; 2;;]`または`B = [1;;]`。
  * `c::AbstractVector{<:Real}`: ベクトルである必要があります。退化したスカラー`c`は、最初にベクトル形式に変換する必要があります。例：`c = [0]`。
  * `A::AbstractMatrix{<:Real}`: 行列である必要があります。退化したベクトルまたはスカラー`A`は、最初に行列形式に変換する必要があります。例：`A = [1 2]`、`A = [1; 2;;]`または`A = [-1;;]`。
  * `C::AbstractMatrix{<:Real}`: 行列である必要があります。退化したベクトルまたはスカラー`C`は、最初に行列形式に変換する必要があります。例：`C = [1 2]`、`C = [1; 2;;]`または`C = [-1;;]`。
  * `Sx::Vector{<:BasicDomain}`: 非負の実数空間または非負の混合整数空間であることが許可されます。次の3つの基本データ型のインスタンスの（混合）ベクトルとして構築する必要があります：`Rplus`、`ZeroOne`および`Zplus`。例：`Sy = [ZeroOne()]`は1次元のバイナリ空間`{0, 1}`を示し、`Sy = [Rplus(2), Zplus(3)]`は5次元の非負の混合整数空間`ℝ₊² × ℤ₊³`を示します。後者は`Sy = [fill(Rplus(), 2), fill(Zplus(), 3)]`と同等です。
  * `Sy::Vector{<:BasicDomain}`: 非負の実数空間であることが許可されます。構築方法は`Sx`と似ています。
  * `U::Union{Model, Polyhedron}`: 不確実性集合は、`JuMP.jl`パッケージを使用して`Model`として構築するか、`Polyhedra.jl`パッケージを使用して`Polyhedron`として構築することが許可されます。このパッケージは、`JuMP.jl`、`Polyhedra.jl`およびその他の関連パッケージからいくつかの必要な関数を統合しており、ユーザーが上記のパッケージを追加で`using/import`することなく不確実性集合を便利にモデル化できるようにします。使用の簡単な例については`Examples`セクションを参照してください。`JuMP`モデルの不確実性集合で`u`として登録された名前の変数のみが不確実性変数として認識されます。ただし、登録された変数名が1つだけの場合（またはすべての変数が匿名の場合）を除きます。

# キーワード

  * `MPsolver::Module = HiGHS`: マスタープロブレム（`MP`）のソルバーです。`Sx`および`Sy`のタイプに基づいて選択する必要があります。一般的に、`Sx`または`Sy`が混合整数空間である場合、混合整数線形プログラム（MILP）をサポートするソルバーである必要があります。
  * `SPsolver::Module = HiGHS`: KKT条件に基づく再定式化形式のサブプロブレム（`SP`）のソルバーです（実行可能性オラクルと最適性オラクルの両方）。サブプロブレムオラクルはビッグM法に基づく線形化された再定式化であるため、`U`が単に多面体の不確実性集合である場合、少なくともMILPソルバーである必要があります。
  * `ϵ::Real = 1e-5`: 拡張CCG法の全体的な絶対停止基準です。これは、オラクルの目的値が`ϵ`未満でない場合、現在の`x`が実行不可能であると考える実行可能性オラクルの許容範囲としても使用されます。
  * `BigM::Real = 1e5`: ビッグM法に基づく`SP`のビッグM値（実行可能性オラクルと最適性オラクルの両方）。ビッグMに対して厳密な上限が解析的に得られる場合、アルゴリズムのパフォーマンスが向上します。
  * `verbose::Bool = true`: 解決プロセスの詳細出力を制御するスイッチです。

# 戻り値

この関数は、次の順序でエントリを持つ`Tuple{Vector{Real}, Real, Integer}`を返します：

  * `x::Vector{Real}`: 第一段階の決定変数`x`の最適解。
  * `objv::Real`: 二段階ロバスト最適化問題の最適目的値。
  * `k::Integer`: 解決プロセスが終了するまでの総反復回数。

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
y, objv = SolveTwoStageRO_ECCG(c, b, A, d, G, h, E, M, Sy, Sx, UncMod)
# # `Polyhedron`型の不確実性集合で関数を呼び出す：
# UncSet = polyhedron(HalfSpace([1], 1) ∩ HalfSpace([-1], 0))
# y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
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
y, objv = SolveTwoStageRO_ECCG(c, b, A, d, G, h, E, M, Sy, Sx, UncMod)
# # `Polyhedron`型の不確実性集合で関数を呼び出す：
# UncSet = polyhedron(UncMod, CDDLib.Library(:exact))
# ind_δ = ind_of_var(UncMod, "δ")
# UncSet = eliminate(UncSet, ind_δ)
# y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
```

# 参考文献

1. Bertsimas, D., & Shtern, S. (2018). A scalable algorithm for two-stage adaptive linear optimization. arXiv preprint arXiv:1807.02812.

```
