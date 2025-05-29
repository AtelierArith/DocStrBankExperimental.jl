```
plotxy(x, y; size = (500, 300), color = nothing, ellipse::Bool = false, 
    prob = .95, circle::Bool = false, bisect::Bool = false, zeros::Bool = false,
    xlabel = "", ylabel = "", title = "", kwargs...)
plotxy(x, y, group; size = (600, 350), color = nothing, ellipse::Bool = false, 
    prob = .95, circle::Bool = false, bisect::Bool = false, zeros::Bool = false,
    xlabel = "", ylabel = "", title = "", leg::Bool = true, leg_title = "Group", 
    kwargs...)
```

Scatter plot of (x, y) data

  * `x` : A x-vector (n).
  * `y` : A y-vector (n).
  * `group` : Categorical variable defining groups (n).

Keyword arguments:

  * `size` : Size (horizontal, vertical) of the figure.
  * `color` : Set color(s). If `group` if used, `color` must be    a vector of same length as the number of levels in `group`.
  * `ellipse` : Boolean. Draw an ellipse of confidence,    assuming a Ch-square distribution with df = 2. If `group`    is used, one ellipse is drawn per group.
  * `prob` : Probability for the ellipse of confidence.
  * `bisect` : Boolean. Draw a bisector.
  * `zeros` : Boolean. Draw horizontal and vertical axes passing    through origin (0, 0).
  * `xlabel` : Label for the x-axis.
  * `ylabel` : Label for the y-axis.
  * `title` : Title of the graphic.
  * `leg` : Boolean. If `group` is used, display a legend    or not.
  * `leg_title` : Title of the legend.
  * `kwargs` : Optional arguments to pass in function `scatter`    of Makie.

To use `plotxy`, a backend (e.g. CairoMakie) has  to be specified.

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X 
y = dat.Y.tbc
year = dat.Y.year
tab(year)
lev = mlev(year)
nlev = length(lev)

model = pcasvd(nlv = 5)  
fit!(model, X) 
@head T = model.fitm.T

plotxy(T[:, 1], T[:, 2]; color = (:red, .5)).f

plotxy(T[:, 1], T[:, 2], year; ellipse = true, xlabel = "PC1", ylabel = "PC2").f

i = 2
colm = cgrad(:Dark2_5, nlev; categorical = true)
plotxy(T[:, i], T[:, i + 1], year; color = colm, xlabel = string("PC", i), 
    ylabel = string("PC", i + 1), zeros = true, ellipse = true).f

plotxy(T[:, 1], T[:, 2], year).lev

plotxy(1:5, 1:5).f

y = reshape(rand(5), 5, 1)
plotxy(1:5, y).f

## Several layers can be added
## (same syntax as in Makie)
A = rand(50, 2)
f, ax = plotxy(A[:, 1], A[:, 2]; xlabel = "x1", ylabel = "x2")
ylims!(ax, -1, 2)
hlines!(ax, 0.5; color = :red, linestyle = :dot)
f
```
