```
LDataSet <: AbstractDataSet
```

A template for generating datasets with parameterized naming patterns.

# Fields

  * `format`: Format string pattern for the dataset name
  * `data`: Dictionary of variable patterns
  * `metadata`: Additional metadata

# Examples

```julia
using SPEDAS.MMS

# Access FPI dataset specification
lds = mms.datasets.fpi_moms

# Create a concrete dataset with specific parameters
ds = DataSet(lds; probe=1, data_rate="fast", data_type="des")
```

The format string and variable patterns use placeholders like `{probe}`, `{data_rate}`,  which are replaced with actual values when creating a concrete `DataSet`.
