```
intersection(H1::AbstractHyperrectangle, H2::AbstractHyperrectangle)
```

Compute the intersection of two hyperrectangular sets.

### Input

  * `H1` – hyperrectangular set
  * `H2` – hyperrectangular set

### Output

If the hyperrectangular sets do not intersect, the result is the empty set. Otherwise the result is the hyperrectangle that describes the intersection.

### Algorithm

In each isolated direction `i` we compute the rightmost left border and the leftmost right border of the hyperrectangular sets. If these borders contradict, then the intersection is empty. Otherwise the resulting hyperrectangle uses these borders in each dimension.
