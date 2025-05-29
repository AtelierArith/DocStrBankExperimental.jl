```
rec_matrix_motifs(rec_matrix::RecurrenceMatrix;seqs="recurrences",window_range=collect(1:6),n_motifs=2)
```

Returns set of probabilities associated with consecutive runs in off-diagonals.

Argument `seqs` sets the type of consecutive sequences: either 'double' (recurrences and non-recurrences),  'recurrences' or 'poincare' (non-recurrences).  The diagonals given by `window_range` argument are considered, along with n*motifs for each diagonal.  See `AnalyticComb.weighted*bin*runs*prob` for definition of symbolic construction.  
