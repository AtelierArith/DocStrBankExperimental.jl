```
  cormat(ArrayName, RankOrder=1)
```

Cormat calculates a symetric correlation matrix using both PPMC and Rank Order. Rank Order is default because this is what it used in the Iman-Conover method for correlating of simulated variables.

`RankOrder = 1` calculates the Spearman rank order correlation used in MCHammer (this argument is optional and defaults to Spearman)

`RankOrder = 0` calculates the Pearson Product Moment Correlation
