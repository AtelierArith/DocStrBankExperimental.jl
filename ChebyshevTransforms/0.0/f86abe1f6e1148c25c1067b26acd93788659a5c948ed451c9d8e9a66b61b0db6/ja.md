```
paduatransform!(coeffs, P::PaduaTransformPlan, vals[, lex])
```

与えられた値 `vals` がパデュア点で評価された場合、パデュア変換を介して2Dのチェビシェフ多項式の係数を取得します。係数は `coeffs` に書き込まれ、これは行列、ベクトル、またはそのいずれかの反復可能なものである必要があります。

`vals` ベクトルの反復可能な集合と、それに対応する `coeffs` 行列またはベクトルの反復可能な集合が与えられた場合、各 `vals` ベクトルは多次元パデュア変換で別々に変換されます。

`lex` は、`out` がベクトルの場合に係数がどの順序で `out` に書き込まれるかを決定します。詳細については [`fromcoeffsmat!`](@ref) を参照してください。

!!! warning
    `coeffs` が行列の場合、右下の対角線のすべてのエントリがゼロであることを確認してください。これらは上書きされません。


# 例

```jldoctest
julia> plan = PaduaTransformPlan{Float64}(2);

julia> f(x, y) = 3 + 4x + 5 * x*y, 6 + 7y
f (generic function with 1 method)

julia> vals = getpaduapoints(f, 2)
6×2 Matrix{Float64}:
 12.0  13.0
  4.5   2.5
  3.0   9.5
  3.0  -1.0
 -6.0  13.0
  1.5   2.5

julia> paduatransform!(zeros(3, 3), plan, vals[:, 1])
3×3 Matrix{Float64}:
 3.0  4.0  0.0
 0.0  5.0  0.0
 0.0  0.0  0.0

julia> paduatransform!(zeros(6), plan, vals[:, 2], Val(true))
6-element Vector{Float64}:
 6.0
 0.0
 7.0
 0.0
 0.0
 0.0

julia> paduatransform!((zeros(3, 3), zeros(3, 3)), plan, vals)
([3.0 4.0 0.0; 0.0 5.0 0.0; 0.0 0.0 0.0], [6.0 0.0 0.0; 7.0 0.0 0.0; 0.0 0.0 0.0])
```
