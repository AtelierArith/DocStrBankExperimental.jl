```
find_motifs(ts, w, d)
```

Given a motif of shape 'shape' (array{any,1}), look for all the repetitions of it which differ only up to 'd' differences. Input:

```
ts : time-series in which to look for motifs
shape : shape (aray{any,1}) of the motif to look for.
d : allowed errors (differences) between motifs
```

returns :     motif : an instance of 'pattern' containing the found repetition of the input 'shape'.
