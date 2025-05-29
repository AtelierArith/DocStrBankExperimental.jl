```
Data(), Facet()
```

Create a Data/Facet element. [Vega docs](https://vega.github.io/vega/docs/data/)

Arguments can be named arguments describing the data structure. All Julia objects  thta comply with the Tables interface can be used as values. 

# Examples

```julia
using DataFrames
N = 100
tb = DataFrame(x=randn(N), y=randn(N), a=rand("ABC", N))

mydata = Data(values=tb)
```
