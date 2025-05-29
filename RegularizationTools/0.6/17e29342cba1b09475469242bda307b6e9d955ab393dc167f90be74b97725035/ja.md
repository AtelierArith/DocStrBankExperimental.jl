```
function invert(A::Matrix, b::Vector, method::InverseMethod; kwargs...)
```

Tikhonov反転を実行するための高レベルAPI関数です。この関数は代数データ型InverseMethodを使用します。

```julia
    @data InverseMethod begin 
        Lₖ(Int)                            # 純粋なTikhonov
        Lₖx₀(Int,Vector)                   # 初期推定値あり
        LₖB(Int,Vector,Vector)             # 制約付き
        Lₖx₀B(Int,Vector,Vector,Vector)    # 初期推定値 + 制約付き
        LₖDₓ(Int,Float64)                  # フィルタ付き 
        Lₖx₀Dₓ(Int,Vector,Float64)         # 初期推定値 + フィルタ付き 
        LₖDₓB(Int,Float64,Vector,Vector)   # フィルタ + 制約付き
        Lₖx₀DₓB(Int,Vector,Float64,Vector,Vector) # 初期推定値 + フィルタ + 制約付き
    end
```

問題を定義し、正しいメソッドにディスパッチします。kwargs...はsolve関数に渡されます。例えば、標準的な二次正則化の方法は次のようになります。

```julia
xλ = @> setupRegularizationProblem(A, 2) solve(b) getfield(:x)
```

これは次のように書き換えることもできます。

```julia
invert(A, b, Lₖ(2))
```

ここで`Lₖ(2)`は二次法を示します。メソッドの命名法は、正則化の順序に対して`Lₖ`、制約付き探索に対して`B`、初期条件に対して`x₀`、HuckleとSedlacek (2012) の二段階データベース正則化に対して`Dₓ`です。メソッドデータ型は探索を初期化するためのハイパーパラメータを取ります。メソッド初期化の例は次の通りです。

```julia
# ハイパーパラメータ 
k: order, lb: low bound, ub: upper bound, ε: noise level, x₀: initial guess
k, lb, ub, ε, x₀ = 2, zeros(8), zeros(8) .+ 50.0, 0.02, 0.5*N

xλ = invert(A, b, Lₖ(k); alg = :gcv_tr, λ₁ = 0.1)
xλ = invert(A, b, Lₖ(k); alg = :gcv_svd, λ₁ = 0.1)
xλ = invert(A, b, LₖB(k, lb, ub); alg = :L_curve, λ₁ = 0.1)
xλ = invert(A, b, Lₖx₀(k, x₀); alg = :L_curve, λ₁ = 0.1)
xλ = invert(A, b, Lₖx₀(k, x₀); alg = :gcv_tr)
xλ = invert(A, b, Lₖx₀(k, x₀); alg = :gcv_svd)
xλ = invert(A, b, Lₖx₀B(k, x₀, lb, ub); alg = :gcv_svd)
xλ = invert(A, b, LₖDₓ(k, ε); alg = :gcv_svd)
xλ = invert(A, b, LₖDₓB(k, ε, lb, ub); alg = :gcv_svd)
xλ = invert(A, b, Lₖx₀Dₓ(k, x₀, ε); alg = :gcv_svd)
xλ = invert(A, b, Lₖx₀DₓB(k, x₀, ε, lb, ub); alg = :gcv_svd)
```
