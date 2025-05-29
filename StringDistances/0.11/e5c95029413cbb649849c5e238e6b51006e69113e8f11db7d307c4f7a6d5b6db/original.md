```
OptimalStringAlignment()
```

Creates the OptimalStringAlignment distance (also known as the restricted DamerauLevenshtein distance).

It is the minimum number of operations (consisting of insertions, deletions or substitutions of a single character, or transposition of two adjacent characters) required to change one string into the other.

The distance differs slightly from the DamerauLevenshtein distance by imposing the restriction that no substring is edited more than once. So for example, "CA" to "ABC" has a distance of 3 by the OptimalStringAlignment distance but a distance of 2 by the DamerauLevenshtein distance. In contrast to the DamerauLevenshtein distance, the OptimalStringAlignment distance does not satisfy the triangle inequality.
