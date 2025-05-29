```
summarizedataCF(d::DataCF)
```

function to summarize the information contained in a DataCF object. It has the following optional arguments:

  * `filename`: if provided, the summary will be saved in the filename, not to screen
  * `pc` (number between (0,1)): threshold of percentage of missing genes to identify 4-taxon subsets with fewer genes than the threshold
