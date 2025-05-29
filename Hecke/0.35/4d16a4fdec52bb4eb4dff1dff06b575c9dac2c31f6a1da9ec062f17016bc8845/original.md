```
reduced_resultant(f::PolyRingElem{T}, g::PolyRingElem{T}) where T <: ResElem{S} where S <: IntegerUnion -> T
```

The reduced resultant of $f$ and $g$ using a quadratic-time algorithm. That is a generator for the $(f, g) \cap Z$
