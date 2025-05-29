```
completed(j::AbstractJob)
```

Return whether the job `j` has completed, i.e., whether `exectime(j) >= cost(j)`.
