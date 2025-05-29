```
ApproxInRegion(sol::AbstractODESolution, p::AbstractVector{<:Number}) -> Bool
```

Blazingly fast approximative test whether a point lies within the polygon defined by the base points of a 2D ODESolution. Especially well-suited for hypothesis testing once a confidence boundary has been explicitly computed.
