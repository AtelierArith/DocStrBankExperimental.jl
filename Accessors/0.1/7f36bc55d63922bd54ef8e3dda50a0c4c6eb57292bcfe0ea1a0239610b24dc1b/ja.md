```
optic₁ ⨟ optic₂
```

ネストされたオブジェクトにアクセスするために、光学 `optic₁`、`optic₂`、...、`opticₙ` を組み合わせます。

# 例

```jldoctest
julia> using Accessors

julia> obj = (a = (b = (c = 1,),),);

julia> la = @optic _.a
       lb = @optic _.b
       lc = @optic _.c
       lens = la ⨟ lb ⨟ lc
(@o _.c) ∘ ((@o _.a.b))

julia> lens(obj)
1
```
