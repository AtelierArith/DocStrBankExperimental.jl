```
markcells(t::Union{Tiler, Table}, cells;
    action = :stroke,
    func = nothing)
```

Mark the cells of Tiler/Table `t` in the `cells`.

By default a box is drawn around the cell using the current settings and filled or stroked according to `action`.

You can supply a function for the `func` keyword that can do anything you want. The function should accept four arguments, `position`, `width`, `height`, and `number`.

## Example

This code draws 30 circles in 5 rows and 6 columns, numbered and colored sequentially in four colors. `getcells()` obtains a selection of the cells from the Tiler.

```julia
@draw begin
    fontsize(30)
    #t = Table(5, 6, 60, 60)
    t = Tiler(400, 400, 5, 6)
    markcells(t, getcells(t, 1:30),
        func = (pos, w, h, n) -> begin
            sethue(["red", "green", "blue", "purple"][mod1(n, end)])
            circle(pos, w / 2, :fill)
            sethue("white")
            text(string(n), pos, halign = :center, valign = :middle)
        end)
end
```
