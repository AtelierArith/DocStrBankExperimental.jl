```
avgseq, results = dba(sequences, dist::DTWDistance; kwargs...)
```

Perfoms DTW Barycenter Averaging (DBA) given a collection of `sequences` and the current estimate of the average sequence.

Example usage:

```
x = [1., 2., 2., 3., 3., 4.]
y = [1., 3., 4.]
z = [1., 2., 2., 4.]
avg,result = dba([x,y,z], DTW(3))
```
