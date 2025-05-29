```julia
canonicalize_clip!(
    state::QuantumClifford.AbstractStabilizer;
    phases
) -> QuantumClifford.AbstractStabilizer

```

安定器のクリップされたゲージを修正します（インプレース）。

入力が有効なフルランクの安定器（すべての演算子が可換で、実数の位相を持つ）であると仮定します。

```jldoctest
julia> s = S"- X_ZX_X
             + XXYZ__
             - YZ_Z_X
             - XZX__Y
             + _Z_Y_Y
             - ____Z_";


julia> canonicalize_clip!(s)
- X_XY__
+ YZY___
+ _XZX__
- _ZYX_Z
- __YZ_X
- ____Z_
```

`phases=false`が設定されている場合、正準化は表における位相を追跡せず、これにより大幅な速度向上が得られます。

[nahum2017quantum](@cite)で導入され、[li2019measurement](@cite)の付録Aにアルゴリズムの詳細な説明があります。

関連情報: [`canonicalize!`](@ref), [`canonicalize_rref!`](@ref), [`canonicalize_gott!`](@ref).
