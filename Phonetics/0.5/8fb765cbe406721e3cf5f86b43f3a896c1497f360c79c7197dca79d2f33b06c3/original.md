```
phnprb(corpus::Array, frequencies::Array, queries::Array; positional=false,
    nchar=1, pad=true)
```

Calculates the phonotactic probability for each item in a list of queries based on a corpus

# Arguments

  * **corpus** The corpus on which to base the probability calculations
  * **frequencies** The frequencies associated with each element in `corpus`
  * **queries** The items for which the probability should be calculated

## Keyword arguments

  * **positional**  Whether to consider where in the query a given phone appears

(e.g., should "K" as the first sound be considered a different category than "K"     as the second sound?)

  * **nchar** The number of characters for each n-gram that will be examined   (e.g., 2 for diphones)
  * **pad** Whether to add padding to each query or not

# Returns

A `DataFrame` with the queries in the first column and the probability values     in the second
