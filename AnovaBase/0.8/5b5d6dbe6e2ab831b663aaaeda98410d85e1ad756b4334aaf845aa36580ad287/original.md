```
AnovaTable
```

A table with coefficients and related statistics of ANOVA. It is mostly modified from `StatsBase.CoefTable`.

# Fields

  * `cols`: values of each statiscics.
  * `colnms`: names of statiscics.
  * `rownms`: names of each row.
  * `pvalcol`: the index of column repressenting p-value.
  * `teststatcol`: the index of column representing test statiscics.

# Constructor

```
AnovaTable(cols::Vector, colnms::Vector, rownms::Vector, pvalcol::Int = 0, teststatcol::Int = 0)
AnovaTable(mat::Matrix, colnms::Vector, rownms::Vector, pvalcol::Int = 0, teststatcol::Int = 0)
```
