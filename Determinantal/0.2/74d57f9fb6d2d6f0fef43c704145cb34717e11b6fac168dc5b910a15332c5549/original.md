```
LazyDist(x)
```

Lazy representation of a distance matrix, meaning that the object can be indexed like a matrix, but the values are computed on-the-fly. This is useful whenever an algorithm only requires some of the entries, or when the dataset is very large.

```@example

x = randn(2, 100)
D = LazyDist(x) #Euclidean dist. by default
D[3, 2] #the getindex method is defined
D = LazyDist(x, (a, b) -> sum(abs.(a - b))) #L1 distance
D[3, 2]
```
