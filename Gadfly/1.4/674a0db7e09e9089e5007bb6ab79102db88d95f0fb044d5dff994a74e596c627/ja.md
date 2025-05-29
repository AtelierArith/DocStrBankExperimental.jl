```
title(ctx::Context, str::String, props::Property...) -> Context
```

プロットのグループにタイトル文字列を追加します。通常、[`vstack`](@ref)、[`hstack`](@ref)、または[`gridstack`](@ref)で作成されます。

# 例

```
p1 = plot(x=[1,2], y=[3,4], Geom.line);
p2 = plot(x=[1,2], y=[4,3], Geom.line);
title(hstack(p1,p2), "my latest data", Compose.fontsize(18pt), fill(colorant"red"))
```
