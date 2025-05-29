```
find_sequence(label::AbstractString, aln::AbstractAlignment)
```

Find sequence with name `label` in `aln`, and return `(index, sequence)`. Scales as the number of sequences. Return the first sequence that matches the label.

!!! Return a *view* of the sequence.
