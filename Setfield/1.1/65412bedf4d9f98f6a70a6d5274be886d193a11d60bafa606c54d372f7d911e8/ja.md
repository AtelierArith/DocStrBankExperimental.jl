```
lens₁ ∘ lens₂
```

レンズ `lens₁`、`lens₂`、...、`lensₙ` を合成してネストされたオブジェクトにアクセスします。

# 例

```jldoctest
julia> using Setfield

julia> obj = (a = (b = (c = 1,),),);

julia> la = @lens _.a
       lb = @lens _.b
       lc = @lens _.c
       lens = la ∘ lb ∘ lc
(@lens _.a.b.c)

julia> get(obj, lens)
1
```
