Allows temporary setting of backend and defaults for Plots. Settings apply only for the `do` block.  Example:

```
Plots.with(:gr, size=(400,400), type=:histogram) do
  plot(rand(10))
  plot(rand(10))
end
```
