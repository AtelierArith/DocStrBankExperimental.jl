```
LazySum{O} <: AbstractVector{O}
```

Type that represents a lazy sum i.e explicit summation is only done when needed.  This type is basically an `AbstractVector` with some extra functionality to calculate things efficiently.

## Fields

  * ops – Vector of summable objects

---

## Constructors

```
LazySum(x::Vector)
```
