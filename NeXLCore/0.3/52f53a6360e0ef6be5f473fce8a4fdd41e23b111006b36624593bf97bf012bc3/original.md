```
loadsmithsoniandata(; clean=false)
```

Load compositional data associated with the Smithsonian Microbeam Standards data set as a DataFrame. Setting clean=true will replace "<0.XXX" with 0.0, replace "missing" with 0.0 and parse string values as Float64.   The data source is https://naturalhistory.si.edu/research/mineral-sciences/collections-overview/reference-materials/smithsonian-microbeam-standards
