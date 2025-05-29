```
dtwplot(seq1, seq2, [dist=SqEuclidean()]; transportcost=1, diagonal=false)
dtwplot(seq1, seq2, D, i1, i2; transportcost=1, diagonal=false)
dtwplot(seq1, seq2, D; transportcost=1, diagonal=false)
```

Given two sequences, perform dynamic time warping and plot the results. If alignment has already been computed, pass the indices `i1` and `i2` to make the plot.

`diagonal = true` plots a diagonal marker as visual aid.
