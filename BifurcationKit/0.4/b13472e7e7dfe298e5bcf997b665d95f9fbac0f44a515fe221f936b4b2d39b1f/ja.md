```julia
struct NewtonPar{T, L<:BifurcationKit.AbstractLinearSolver, E<:BifurcationKit.AbstractEigenSolver}
```

`F(x) = 0` を解く際の `newton` アルゴリズムに影響を与えるパラメータを含む変数を返します。

# 引数（デフォルト値付き）:

  * `tol::Any`: `F(x)` の絶対許容誤差 デフォルト: 1.0e-12
  * `max_iterations::Int64`: ニュートン反復の回数 デフォルト: 25
  * `verbose::Bool`: ニュートン反復を表示しますか？ デフォルト: false
  * `linsolver::BifurcationKit.AbstractLinearSolver`: 線形ソルバー、`<: AbstractLinearSolver` でなければなりません デフォルト: DefaultLS()
  * `eigsolver::BifurcationKit.AbstractEigenSolver`: 固有ソルバー、`<: AbstractEigenSolver` でなければなりません デフォルト: DefaultEig()
  * `linesearch::Bool`: デフォルト: false
  * `α::Any`: デフォルト: convert(typeof(tol), 1.0)
  * `αmin::Any`: デフォルト: convert(typeof(tol), 0.001)

# ラインサーチの引数（アルミホ）

  * `linesearch = false`: ラインサーチアルゴリズムを使用する（すなわち、アルミホのルールによるニュートン）
  * `α = 1.0`: ラインサーチアルゴリズムのためのα（減衰）パラメータの初期値
  * `αmin  = 0.001`: 減衰 `alpha` の最小値

!!! tip "ミューテーション"
    パフォーマンスの理由から、パラメータを保持するために不変の構造体を使用することに決めました。異なるフィールドのミューテーションを大幅に簡素化するために、`Accessors.jl` パッケージを使用できます。例についてはチュートリアルを参照してください。

