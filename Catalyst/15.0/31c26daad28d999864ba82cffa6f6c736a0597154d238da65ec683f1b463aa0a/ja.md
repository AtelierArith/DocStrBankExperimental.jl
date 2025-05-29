```
massactionvector(rn::ReactionSystem, scmap = Dict(); combinatoric_ratelaws = true)
```

各複合体の「質量作用生成物」に対応するエントリを持つベクトルを返します。例えば、複合体 A + B が与えられた場合、ベクトルの対応するエントリは $A*B$ になります。また、複合体 2X + Y の場合、対応するエントリは $X^2*Y$ になります。化学反応ネットワークのODEシステムは $rac{dx}{dt} = Y A_k Φ(x)$ と因数分解でき、ここで $Y$ は [`complexstoichmat`](@ref) であり、$A_k$ は [`laplacianmat`](@ref) の負の値です。このユーティリティは $Φ(x)$ を返します。

デフォルトでは記号ベクトルを返しますが、種の濃度がタプル、ベクトル、または辞書として scmap を介して指定されている場合は数値ベクトルを返します。

`combinatoric_ratelaws` オプションが設定されている場合、それに対する前因子を含めます（[Catalystの反応速度法則の紹介](@ref introduction_to_catalyst_ratelaws)を参照）。システムのデフォルトに従います。

**警告**: 他のCatalyst関数とは異なり、`massactionvector` 関数は記号的な場合に `Vector{Num}` を返します。これはODEの行列分解の計算を容易にするためです。
