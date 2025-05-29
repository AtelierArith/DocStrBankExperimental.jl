```
li1(z::Complex)
```

複素数 $z$ の複素1次ポリログarithm $\operatorname{Li}_1(z) = -\ln(1 - z)$ を返します。$z$ は `Complex` 型です。

実数引数 $z\in\mathbb{R}$ のみを考慮し、実部 $\Re[\operatorname{Li}_1(z)]$ のみを興味がある場合は、より高速な代替手段となる可能性のある関数 [`reli1`](@ref) を参照してください。

他にも [`reli1`](@ref) を参照してください。

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using PolyLog)
julia> li1(1.0 + 1.0im)
-0.0 + 1.5707963267948966im

julia> li1(BigFloat("1.0") + 1im)
-0.0 + 1.570796326794896619231321691639751442098584699687552910487472296153908203143099im
```
