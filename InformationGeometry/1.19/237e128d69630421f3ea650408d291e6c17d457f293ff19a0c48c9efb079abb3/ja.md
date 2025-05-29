```
IntersectRegion(DM::AbstractDataModel,PL::Plane,v::AbstractVector{<:Number},Confnum::Real=1.; N::Int=31) -> Vector{Plane}
```

信頼度レベル `Confnum` の信頼領域と交差するように、`-v` から `+v` までおおよそ移動した `N` 個の平面のファミリーを翻訳します。必要に応じて、平面が削除されたり、より多くの平面が追加されたりして、最大の平面ファミリーが見つかります。
