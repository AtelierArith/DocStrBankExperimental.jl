```
struct CopositiveInner{S} <: PolyJuMP.PolynomialSet
    # PSDコーンの内近似、すなわち通常は
    # `SOSCone`、`DSOSCone`または`SDSOSCone`のいずれか、
    psd_inner::S
end
```

対称行列 $Q$ は、すべてのベクトル $x$ が非負直交体にあるときに $x^{\top} Q x \ge 0$ であればコポジティブである。コポジティビティのチェックはコ-NP完全問題であり [MK87]、このコーンはコポジティブ対称行列のコーンの内近似に過ぎず、これは `psd_inner` のミンコフスキー和と非負エントリを持つ対称行列のコーンによって与えられる [Lemma 3.164, BPT12]。

非負エントリを持つ行列はラグランジュ乗数として解釈できる。例えば、

```julia
@polyvar x y
@constraint(model, x^2 - 2x*y + y^2 in CopositiveInner(SOSCone()))
```

は次のように等価である。

```julia
# コポジティブである必要がある行列
Q = [ 1 -1
     -1  1]
λ = @variable(model, lower_bound=0)
# 非負エントリの対称行列
Λ = [0 λ
     λ 0]
using LinearAlgebra # `Symmetric`のため
@constraint(model, Symmetric(Q - Λ) in PSDCone())
```

これは次のように等価である。

```julia
@polyvar x y
λ = @variable(model, lower_bound=0)
@constraint(model, x^2 - 2x*y + y^2 - 2*λ * x*y in SOSCone())
```

これは、`domain` キーワードを使用すると次のように同じである。

```julia
@polyvar x y
@constraint(model, x^2 - 2x*y + y^2 in SOSCone(), domain = @set x*y ≥ 0)
```

その等価形との重要な違いとして、コポジティブ制約の [`GramMatrixAttribute`](@ref) は行列 `Q` によって与えられるが、`domain` キーワードを使用した等価形では、属性の値は `psd_inner` コーンのグラム行列に対応し、すなわち `Q - Λ` に等しくなるべきである。

[BPT12] Blekherman, G.; Parrilo, P. A. & Thomas, R. R. *半正定値最適化と凸代数幾何学*. Industrial and Applied Mathematics Society, **2012**.

[MK87] K. G. Murty と S. N. Kabadi. *二次および非線形プログラミングにおけるいくつかのNP完全問題*. 数理最適化, 39:117–129, **1987**。
