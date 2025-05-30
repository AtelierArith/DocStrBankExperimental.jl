**`Makie.Toggle <: Block`**

2つの状態を持つスイッチ。

## コンストラクタ

```julia
Toggle(fig_or_scene; kwargs...)
```

## 例

```julia
t_horizontal = Toggle(fig[1, 1])
t_vertical = Toggle(fig[2, 1], orientation = :vertical)
t_diagonal = Toggle(fig[3, 1], orientation = pi/4)
on(t_vertical.active) do switch_is_on
    switch_is_on ? println("おはようございます！") : println("おやすみなさい")
end
```

**属性**

(type `?Makie.Toggle.x` in the REPL for more information about attribute `x`)

`active`, `alignmode`, `buttoncolor`, `cornersegments`, `framecolor_active`, `framecolor_inactive`, `halign`, `height`, `length`, `markersize`, `orientation`, `rimfraction`, `tellheight`, `tellwidth`, `toggleduration`, `valign`, `width`
