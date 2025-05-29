```
pmaximal_overorder(O::AlgAssRelOrd, p::Union{ AbsNumFieldOrderIdeal, RelNumFieldOrderIdeal })
  -> AlgAssRelOrd
```

Returns an order $O'$ containing $O$ such that the index $(O'':O')$ of any maximal order $O''$ containing $O$ is not divisible by $p$ where $p$ is a prime ideal of the base ring of $O$.
