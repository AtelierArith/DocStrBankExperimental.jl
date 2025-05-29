```
Borda <: VotingSystem
```

A Borda count voting system object. The Borda count system assigns a score to each vote according to the following rule:

s = n - r + 1

where s is the score, n is the number of candidates and r is the rank. Effectively, the score reverse codes the rank votes.
