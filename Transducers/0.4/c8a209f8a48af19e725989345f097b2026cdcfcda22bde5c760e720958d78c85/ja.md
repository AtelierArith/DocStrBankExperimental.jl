```
xf'
```

`xf'(rf₁)` は `reducingfunction(xf, rf₁)` を呼び出すためのショートカットです。

より正確には、トランスデューサ `xf` の随伴 `xf′` は *reducing function transform* `rf₁ -> rf₂` です。つまり、`xf'` は reducing function `rf₁` を別の reducing function `rf₂` にマッピングする関数です。

# 例

```jldoctest
julia> using Transducers

julia> y = Map(inv)'(+)(10, 2)
10.5

julia> y == +(10, inv(2))
true
```
