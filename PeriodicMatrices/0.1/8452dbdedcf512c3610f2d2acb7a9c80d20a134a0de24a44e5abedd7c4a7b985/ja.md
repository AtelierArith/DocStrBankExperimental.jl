```
 pseig(A, K = 1; lifting = false, solver, reltol, abstol, dt) -> cm
```

連続時間周期行列の特性乗数を計算します。

与えられた周期 `T` の正方形周期行列 `A(t)` に対して、特性乗数 `cm` はモノドロミー行列 `Ψ = Φ(T,0)` の固有値です。ここで、`Φ(t,τ)` は次の均質線形常微分方程式を満たす状態遷移行列です。

```
dΦ(t,τ)/dt = A(t)Φ(t,τ),  Φ(τ,τ) = I.
```

`lifting = false` の場合、`Ψ` は `K` 個の状態遷移行列の積として計算されます `Ψ = Ψ_K*...*Ψ_1`（関連するキーワード引数を持つ [`monodromy`](@ref) を参照）。固有値は [1] の周期シュア分解法を使用して計算されます。`A` は [`PeriodicFunctionMatrix`](@ref)、[`HarmonicArray`](@ref)、[`PeriodicSymbolicMatrix`](@ref) または [`FourierFunctionMatrix`](@ref) として与えることができます。

`lifting = true` の場合、`Ψ` は（暗黙的に） `Ψ = inv(N)*M` として表現され、ここで `M-λN` は `N` が可逆である正則ペンシルであり、`M-λN` の固有値は行列積 `Ψ := Ψ_K*...*Ψ_1` の固有値と同じです。これは、遷移行列の決定を削減アルゴリズムに組み込む効率的な構造を利用した [2] の手法が採用されており、時折 `K` の大きな値に対して不正確な結果をもたらすことがあります。

*参考文献*

[1] A. Bojanczyk, G. Golub, and P. Van Dooren,      The periodic Schur decomposition. Algorithms and applications, Proc. SPIE 1996.

[2] A. Varga & P. Van Dooren. Computing the zeros of periodic descriptor systems.     Systems and Control Letters, 50:371-381, 2003.
