```
polyportion(p::Vector{Point}, portion=0.5; 
    closed=true,
    pdist = Vector{Union{Float64, Int}}[])
```

Return a portion of a polygon, starting at a value between 0.0 (the beginning) and 1.0 (the end). 0.5 returns the first half of the polygon, 0.25 the first quarter, 0.75 the first three quarters, and so on.

Use `closed=false` to exclude the line joining the final point to the first point from the calculations.

If you already have a list of the distances between each point in the polygon (the "polydistances"), you can pass them in `pdist`, otherwise they'll be calculated afresh, using `polydistances(p, closed=closed)`.

Use the complementary `polyremainder()` function to return the other part.
