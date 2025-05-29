```
detect_motifs(ts, w, d, t = w - d; iters = 1000, tolerance = 0.7)
```

Detects all motifs of length 'w' occuring more often than chance, being identical up to 'd' differences. Input:

```
w : length of motifs to look for
d : allowed errors (differences) between motifs
t : size of the masks to use for random projection in the detection
iters : the numbers of iterations for the random projection process (defaults to 1000)
tolerance : threshold of motif identification.
```

returns :     motifs : a list of motif instances containing all usefull informations about the found motifs (positions, frequency, shapes ...)
