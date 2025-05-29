```
SolveTwoStageRO_MKLCCG(args...; kwargs...)
```

次の二段階ロバスト最適化問題をMultiple Kernel Learning支援のカラムおよび制約生成（MKLCCG）法を使用して解決します：

```formulation
Min_x a' * x + Max_{u ∈ U} Min_{y ∈ Y(x, u)} b' * y

Subject to:

    E * x ≥ e, x ∈ Sx

    Y(x, u) = {y ∈ Sy: A * x + B * y + C * u ≥ c}

    Uは不確実性集合です
```

ここで、`Sx`は非負の実数空間または非負の混合整数空間であることが許可され、`Sy`は非負の実数空間であることが許可されます。

P.S. 我々は実行可能性の仮定が成り立つことを期待しています。すなわち、任意の`u ∈ U`に対して`Y(x, u) ≠ ∅`となるような`x ∈ {x ∈ Sx: E * x ≥ e}`が**存在**しますが、相対的完全回収の仮定（すなわち、任意の`x ∈ {x ∈ Sx: E * x ≥ e}`および任意の`u ∈ U`に対して`Y(x, u) ≠ ∅`）は必ずしも成り立つわけではありません。(`Ref.1`)

# 引数

  * `a::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`a`は最初にベクトル形式に変換する必要があります。例：`a = [2]`。
  * `b::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`b`は最初にベクトル形式に変換する必要があります。例：`b = [1]`。
  * `E::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`E`は最初に行列形式に変換する必要があります。例：`E = [1 2]`、`E = [1; 2;;]`または`E = [0;;]`。
  * `e::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`e`は最初にベクトル形式に変換する必要があります。例：`e = [0]`。
  * `B::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`B`は最初に行列形式に変換する必要があります。例：`B = [1 2]`、`B = [1; 2;;]`または`B = [1;;]`。
  * `c::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`c`は最初にベクトル形式に変換する必要があります。例：`c = [0]`。
  * `A::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`A`は最初に行列形式に変換する必要があります。例：`A = [1 2]`、`A = [1; 2;;]`または`A = [-1;;]`。
  * `C::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`C`は最初に行列形式に変換する必要があります。例：`C = [1 2]`、`C = [1; 2;;]`または`C = [-1;;]`。
  * `Sx::Vector{<:BasicDomain}`: 非負の実数空間または非負の混合整数空間であることが許可されます。次の3つの基本データ型のインスタンスの（混合）ベクトルとして構築する必要があります：`Rplus`、`ZeroOne`および`Zplus`。例：`Sx = [ZeroOne()]`は1次元のバイナリ空間`{0, 1}`を示し、`Sx = [Rplus(2), Zplus(3)]`は5次元の非負の混合整数空間`ℝ₊² × ℤ₊³`を示します。後者は`Sx = [fill(Rplus(), 2), fill(Zplus(), 3)]`と同等です。
  * `Sy::Vector{<:BasicDomain}`: 非負の実数空間であることが許可されます。構築方法は`Sx`と似ています。
  * `U::Union{StandardModel, CombinedModel, Vector{StandardModel}}`: 不確実性集合は、[`MKLOneClassSVM.jl`](https://github.com/hanb16/MKLOneClassSVM.jl)パッケージを使用して`StandardModel`、`CombinedModel`または`Vector{StandardModel}`として構築することが許可されます。このパッケージは、ユーザーがこのパッケージを追加で`using/import`することなく、不確実性集合を便利にモデル化できるようにするために、`MKLOneClassSVM.jl`からいくつかの必要な関数を統合しています。使用方法の簡単な説明については`Examples`セクションを参照してください。

# キーワード

  * `MPsolver::Module = HiGHS`: マスタープロブレム（`MP`）のソルバーです。`Sx`および`Sy`のタイプに基づいて選択する必要があります。一般的に、`Sx`または`Sy`が混合整数空間である場合、混合整数線形プログラム（MILP）をサポートするソルバーである必要があります。
  * `SPsolver::Module = HiGHS`: KKT条件に基づく再定式化形式のサブプロブレム（`SP`）のソルバーです（実行可能性オラクルと最適性オラクルの両方）。サブプロブレムオラクルはビッグM法に基づく線形化された再定式化であるため、`U`が単に多面体不確実性集合である場合、少なくともMILPソルバーである必要があります。
  * `ϵ::Real = 1e-5`: 拡張CCG法の全体的な絶対停止基準です。これは、オラクルの目的値が`ϵ`未満でない場合、現在の`x`が実行不可能であると考える実行可能性オラクルの許容誤差としても使用されます。
  * `BigM::Real = 1e5`: ビッグM法に基づく線形化された再定式化における`SP`のビッグM値（実行可能性オラクルと最適性オラクルの両方）。ビッグMに対して厳密な境界が解析的に得られる場合、アルゴリズムのパフォーマンスが向上します。
  * `verbose::Bool = true`: 解決プロセスの詳細な出力を制御するスイッチです。

# 戻り値

この関数は、次の順序でエントリを持つ`Tuple{Vector{Real}, Real, Integer}`を返します：

  * `x::Vector{Real}`: 第一段階の決定変数`x`の最適解。
  * `objv::Real`: 二段階ロバスト最適化問題の最適目的値。
  * `k::Integer`: 解決プロセスが終了するまでの総反復回数。

# 例

### ケース-1:

```julia
using MKLTwoStageRO
using GLMakie # ユーザーが視覚化を希望する場合

# 不確実データ生成
u1 = 0.5 .+ 4 * rand(300)
u2 = 2 ./ u1 + 0.3 * randn(300) .+ 1
X = [u1'; u2']

# MKLベースの不確実性集合構築
algor = HessianMKL(verbose=false)
U = mklocsvmtrain(X, 21; kernel="DPDK", algorithm=algor, q_mode="randomly", ν=0.01, μ=0.05)
mklocsvmplot(U; backend=GLMakie) # MKL不確実性集合を視覚化

# 二段階ROモデルのインスタンス化
a = [400, 414, 326, 18, 25, 20]
b = [22, 33, 20, 33, 23, 25]
E = [5 0 0 -1 0 0; 0 5 0 0 -1 0; 0 0 5 0 0 -1]
e = [0.0, 0.0, 0.0]
B = [-1.0 0.0 0.0 -1.0 0.0 0.0; 0.0 -1.0 0.0 0.0 -1.0 0.0; 0.0 0.0 -1.0 0.0 0.0 -1.0; 1.0 1.0 1.0 0.0 0.0 0.0; 0.0 0.0 0.0 1.0 1.0 1.0]
c = [0.0, 0.0, 0.0, 0.0, 0.0]
A = [0.0 0.0 0.0 1.0 0.0 0.0; 0.0 0.0 0.0 0.0 1.0 0.0; 0.0 0.0 0.0 0.0 0.0 1.0; 0.0 0.0 0.0 0.0 0.0 0.0; 0.0 0.0 0.0 0.0 0.0 0.0]
C = [0.0 0.0; 0.0 0.0; 0.0 0.0; -1.0 0.0; 0.0 -1.0]
Sx = [ZeroOne(3), Rplus(3)]
Sy = [Rplus(6)]

# モデルを解決するために関数を呼び出す
y, objv = SolveTwoStageRO_MKLCCG(a, b, E, e, B, c, A, C, Sx, Sy, U)
```

### ケース-2:

```julia
using Distributed # ユーザーが並列化を希望する場合
addprocs(5)
@everywhere using MKLTwoStageRO
using GLMakie # ユーザーが視覚化を希望する場合

# 不確実データ生成
u1 = 0.5 .+ 4 * rand(300)
u2 = 2 ./ u1 + 0.3 * randn(300) .+ 1
X = [u1'; u2']

# MKLベースの不確実性集合構築
algor = HessianMKL(verbose=false)
U = mklocsvmtrain(X, 50; kernel="DPDK", algorithm=algor, q_mode="randomly", ν=0.01, μ=0.05, num_batch=5)
mklocsvmplot(U; backend=GLMakie) # MKL不確実性集合を視覚化

# 二段階ROモデルのインスタンス化
a = [400, 414, 326, 18, 25, 20]
b = [22, 33, 20, 33, 23, 25]
E = [5 0 0 -1 0 0; 0 5 0 0 -1 0; 0 0 5 0 0 -1]
e = [0.0, 0.0, 0.0]
B = [-1.0 0.0 0.0 -1.0 0.0 0.0; 0.0 -1.0 0.0 0.0 -1.0 0.0; 0.0 0.0 -1.0 0.0 0.0 -1.0; 1.0 1.0 1.0 0.0 0.0 0.0; 0.0 0.0 0.0 1.0 1.0 1.0]
c = [0.0, 0.0, 0.0, 0.0, 0.0]
A = [0.0 0.0 0.0 1.0 0.0 0.0; 0.0 0.0 0.0 0.0 1.0 0.0; 0.0 0.0 0.0 0.0 0.0 1.0; 0.0 0.0 0.0 0.0 0.0 0.0; 0.0 0.0 0.0 0.0 0.0 0.0]
C = [0.0 0.0; 0.0 0.0; 0.0 0.0; -1.0 0.0; 0.0 -1.0]
Sx = [ZeroOne(3), Rplus(3)]
Sy = [Rplus(6)]

# モデルを解決するために関数を呼び出す
y, objv = SolveTwoStageRO_MKLCCG(a, b, E, e, B, c, A, C, Sx, Sy, U)
```

# 参考文献

1. Han, B. (2024). Multiple kernel learning-aided column-and-constraint generation method.
2. Han, B., Shang, C., & Huang, D. (2021). Multiple kernel learning-aided robust optimization: Learning algorithm, computational tractability, and usage in multi-stage decision-making. European Journal of Operational Research, 292(3), 1004-1018.
