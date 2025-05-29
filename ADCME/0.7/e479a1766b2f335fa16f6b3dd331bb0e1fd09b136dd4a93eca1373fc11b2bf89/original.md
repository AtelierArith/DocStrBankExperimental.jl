```
animate(update::Function, frames; kwargs...)
```

Creates an animation using update function `update`. 

# Example

```julia
θ = LinRange(0, 2π, 100)
x = cos.(θ)
y = sin.(θ)
pl, = plot([], [], "o-")
t = title("0")
xlim(-1.2,1.2)
ylim(-1.2,1.2)
function update(i)
    t.set_text("$i")
    pl.set_data([x[1:i] y[1:i]]'|>Array)
end
animate(update, 1:100)
```
