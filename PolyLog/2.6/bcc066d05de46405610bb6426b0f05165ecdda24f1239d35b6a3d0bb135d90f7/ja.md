```
li4(z::Complex)
```

複素数 $z$ の複素4次ポリログarithm $\operatorname{Li}_4(z)$ を返します。$z\in\mathbb{R}$ の実引数のみを考慮し、4次ポリログarithm の実部 $\Re[\operatorname{Li}_4(z)]$ のみを興味がある場合は、より高速な代替手段となる可能性のある関数 [`reli4`](@ref) を参照してください。

また、[`reli4`](@ref) も参照してください。

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using PolyLog)
julia> li4(1.0 + 1.0im)
0.9593189135784194 + 1.138039196676983im
```
