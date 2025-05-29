```
TSROModel(fields...)
```

次の二段階ロバスト最適化モデルのインスタンスを作成します（詳細は`Ref.1`の`(1)`を参照）：

```formulation
Min_y c' * y + Max_{u ∈ U} Min_{x ∈ F(y, u)} b' * x

Subject to:

    A * y ≥ d, y ∈ Sy

    F(y, u) = {x ∈ Sx: G * x ≥ h - E * y - M * u}

    Uは不確実性集合です
```

ここで、`Sy`と`Sx`は非負の実数空間または非負の混合整数空間であることが許可されています。

P.S. 次の穏やかな仮定が成り立つことを期待しています（`Ref.1-2`）：

  * `Sx`が非負の実数空間であるときの相対的完全回収の仮定、すなわち、第二段階の意思決定問題（線形計画問題）は、与えられた`y`と`u`に対して常に実行可能です。
  * `Sx`が非負の混合整数空間であるとき、少なくとも1つの実数次元を持つこと、すなわち、混合整数プログラミングの回収問題には少なくとも1つの連続回収変数があります。
  * `Sx`が非負の混合整数空間であるときの拡張相対的完全回収特性、すなわち、`y`、`u`、および`x`の整数部分を固定することによって得られる問題（線形計画問題）は常に実行可能で有界です。
  * `Sx`が非負の混合整数空間であるとき、離散回収変数の実行可能集合（すなわち、`x`の整数部分）は有界です。

# フィールド

  * `c::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`c`は最初にベクトル形式に変換する必要があります。例：`c = [2]`。
  * `b::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`b`は最初にベクトル形式に変換する必要があります。例：`b = [1]`。
  * `A::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`A`は最初に行列形式に変換する必要があります。例：`A = [1 2]`、`A = [1; 2;;]`または`A = [0;;]`。
  * `d::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`d`は最初にベクトル形式に変換する必要があります。例：`d = [0]`。
  * `G::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`G`は最初に行列形式に変換する必要があります。例：`G = [1 2]`、`G = [1; 2;;]`または`G = [1;;]`。
  * `h::AbstractVector{<:Real}`: ベクトルである必要があります。退化スカラー`h`は最初にベクトル形式に変換する必要があります。例：`h = [0]`。
  * `E::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`E`は最初に行列形式に変換する必要があります。例：`E = [1 2]`、`E = [1; 2;;]`または`E = [-1;;]`。
  * `M::AbstractMatrix{<:Real}`: 行列である必要があります。退化ベクトルまたはスカラー`M`は最初に行列形式に変換する必要があります。例：`M = [1 2]`、`M = [1; 2;;]`または`M = [-1;;]`。
  * `Sy::Vector{<:BasicDomain}`: 非負の実数空間または非負の混合整数空間であることが許可されています。次の3つの基本データ型のインスタンスの（混合）ベクトルとして構築する必要があります：`Rplus`、`ZeroOne`および`Zplus`。例：`Sy = [ZeroOne()]`は1次元のバイナリ空間`{0, 1}`を示し、`Sy = [Rplus(2), Zplus(3)]`は5次元の非負混合整数空間`ℝ₊² × ℤ₊³`を示します。後者は`Sy = [fill(Rplus(), 2), fill(Zplus(), 3)]`と同等です。
  * `Sx::Vector{<:BasicDomain}`: 非負の実数空間または非負の混合整数空間であることが許可されています。次の3つの基本データ型のインスタンスの（混合）ベクトルとして構築する必要があります：`Rplus`、`ZeroOne`および`Zplus`。構築方法は`Sy`と同じです。
  * `U::Union{Model, Polyhedron, StandardModel, CombinedModel, Vector{StandardModel}}`: 不確実性集合は、`JuMP.jl`パッケージを使用して`Model`として構築するか、`Polyhedra.jl`パッケージを使用して`Polyhedron`として構築するか、または[`MKLOneClassSVM.jl`](https://github.com/hanb16/MKLOneClassSVM.jl)パッケージを使用して`StandardModel`、`CombinedModel`または`Vector{StandardModel}`として構築することが許可されています。このパッケージは、ユーザーが上記のパッケージを追加で`using/import`することなく、不確実性集合を便利にモデル化できるように、`JuMP.jl`、`Polyhedra.jl`、`MKLOneClassSVM.jl`およびその他の関連パッケージからいくつかの必要な関数を統合しています。簡単な使用法については`Examples`セクションを参照してください。P.S.: 1. `JuMP`モデルの不確実性集合で`u`として登録された名前の変数のみが不確実性変数として認識されます。ただし、登録された変数名が1つだけの場合（またはすべての変数が匿名の場合）を除きます。2. 不確実性集合がMKLベースのものである場合、ユーザーはそれを解決するために`MKLCCG`アルゴリズムを指定する必要があります。

# 参考文献

1. Zeng, B., & Zhao, L. (2013). Solving two-stage robust optimization problems using a column-and-constraint generation method. Operations Research Letters, 41(5), 457-461.
2. Zhao, L., & Zeng, B. (2012). An exact algorithm for two-stage robust optimization with mixed integer recourse problems. submitted, available on Optimization-Online. org.
3. Bertsimas, D., & Shtern, S. (2018). A scalable algorithm for two-stage adaptive linear optimization. arXiv preprint arXiv:1807.02812.
4. Han, B. (2024). Multiple kernel learning-aided column-and-constraint generation method.
5. Han, B., Shang, C., & Huang, D. (2021). Multiple kernel learning-aided robust optimization: Learning algorithm, computational tractability, and usage in multi-stage decision-making. European Journal of Operational Research, 292(3), 1004-1018.
