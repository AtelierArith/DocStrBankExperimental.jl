```
Mosaic(T::Type, S::Type)
```

Data structure for generating a mosaic plot, a comparison between two categorical variables.

# Example

```
using OnlineStats, Plots
x = [rand() > .8 for i in 1:10^5]
y = rand([1,2,2,3,3,3], 10^5)
o = fit!(Mosaic(Bool, Int), zip(x, y))
plot(o)
```
