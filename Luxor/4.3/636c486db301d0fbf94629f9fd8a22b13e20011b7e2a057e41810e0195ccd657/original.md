The Luxor package provides a set of vector drawing functions for creating graphical documents.

```julia
@draw begin
    circle(Point(0, 0), 100, :stroke)
    text("Hello World")
end
```
