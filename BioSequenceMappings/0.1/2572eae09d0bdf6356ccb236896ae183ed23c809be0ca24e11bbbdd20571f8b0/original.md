```
match_sequences(pattern, aln::AbstractAlignment)
```

Find sequences whose name matches `label` in `aln`, and return `(indices, sequences)`. Sequences are returned as columns.

!!! Return a *view* of the sequences.
