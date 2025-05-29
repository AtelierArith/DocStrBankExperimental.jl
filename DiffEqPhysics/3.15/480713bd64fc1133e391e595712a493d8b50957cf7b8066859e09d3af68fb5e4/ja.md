```
HamiltonianProblem(H, p0, q0, tspan, param=nothing; kwargs...)
HamiltonianProblem((dp, dq), p0, q0, tspan, param=nothing; kwargs...)
```

物理システムをそのハミルトニアン関数 `H(p, q, param)` または関数ペア `dp = -∂H/∂q` と `dq = ∂H/∂p` によって定義します。

運動方程式は次のように与えられます： `q̇ = ∂H/∂p = dq` および `ṗ  = -∂H/∂q = dp`。

正準インパルスの初期値 `p0` と座標 `q0` はスカラー、`SArray` または他の `AbstractArray` である可能性があります。これらの型は、関数 `dp` と `dq` の型を決定します。

最初の2つのケースでは、導関数関数は `dp(p, q, param, t)` および `dq(p, q, param, t)` のシグネチャを必要とし、後者のケースでは部分導関数は、事前に定義された配列 `Δp` と `Δq` を使用して、変異シグネチャ `dp!(Δp, p, q, param, t)` および `dq!(Δq, p, q, param, t)` を使用します。

ハミルトニアン関数が与えられている場合、`dp` と `dq` は自動的にAD（`ForwardDiff`）を使用して計算されます。

!!! note



`H` は時間を第4引数として持つ場合と持たない場合の両方で定義できます。両方のメソッドが定義されている場合は、4つの引数を持つ方が使用されます。
