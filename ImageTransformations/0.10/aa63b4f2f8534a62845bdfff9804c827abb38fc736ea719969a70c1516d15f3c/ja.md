```
InvWarpedView(img, tinv, [indices]; kwargs...) -> wv
InvWarpedView(inner_view, tinv) -> wv
```

`img`のビューを作成し、`wv[I]`に渡された任意のインデックス`I`を遅延的に変換するので、`wv[I] == img[inv(tinv)(I)]`となります。

遅延評価を除けば、以下の2行は同等であると期待されます：

```julia
warp(img, inv(tform), [indices]; kwargs...)
invwarpedview(img, tform, [indices]; kwargs...)
```

[`WarpedView`](@ref)との概念的な違いは、`InvWarpedView`がインデックスについて考えるよりも画像について考える方が便利な場合に使用されることです。さらに、`InvWarpedView`は変換の単純なネストを可能にし、その場合、変換は1つのものに合成されます。

warp、関連する引数およびパラメータの詳細な説明については、[`warp`](@ref)を参照してください。
