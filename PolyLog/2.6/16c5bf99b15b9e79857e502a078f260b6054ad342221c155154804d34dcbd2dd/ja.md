```
li3(z::Complex)
```

複素数 $z$ の複素三重対数 $\operatorname{Li}_3(z)$ を返します。$z$ は `Complex` 型です。

実数引数 $z\in\mathbb{R}$ のみを考慮し、三重対数の実部 $\Re[\operatorname{Li}_3(z)]$ のみを興味がある場合は、より高速な代替手段となる可能性のある関数 [`reli3`](@ref) を参照してください。

他にも [`reli3`](@ref) を参照してください。

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using PolyLog)
julia> li3(1.0 + 1.0im)
0.8711588834109381 + 1.267083441888924im
```
