Decompose permutation into adjacent transpositions using insertion sort.

An *adjacent transposition*, also known as a *simple transposition*, is a transposition of form (i i+1), represented here as simply the number i.

Bubble sort and insertion sort are, in a sense, dual algorithms (Knuth, TAOCP, Vol 3: Searching and Sort, Sec 5.3.4: Networks for sorting, Figures 45 & 46). A minimal example on which they give different decompositions is the permutation:

[1,2,3] ↦ [3,2,1]

See also: [`adjacent_transpositions_by_bubble_sort!`](@ref).
