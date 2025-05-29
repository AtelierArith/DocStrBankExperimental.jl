```
prepareData(df, confounderEps, confounderCov)
prepareData("path/to/filename.csv", confounderEps, confounderCov)
```

Prepare Data Creates the latent confounding structure from the object labels in the data. Parses matrices for the observed covariates, treatments, and outcomes.

Returns: `X, T, Y, SigmaU`
