```
mkbatch(file::String; 
        delim = '	',
        data_table = SampleDataTable,
        signal_table = SampleDataTable,
        conc_table = SampleDataTable,
        data_config = Dict{Symbol, Any}(), 
        signal_config = Dict{Symbol, Any}(), 
        conc_config = Dict{Symbol, Any}(), 
        method_config = Dict{Symbol, Any}()
        )
```

Create a template directory of a batch. See "README.md" for available keys and values for config.

The default table wrapper is `SampleDataTable`, whose default sample column name is "Sample", and default sample column name for levels is "Level". The default analyte column name for `AnalyteDataTable` is "Analyte".

The priorities of default analytes are `conc_config[:Analyte]`, `signal_config[:Analyte]`, `data_config[:Analyte]`, and lastly `["Analyte1", "Analyte2"]`. The default samples for data are `["S1", "S2"]`. The default calibration points are `["C1", "C2", "C3", "C4", "C5"]`. The default calibration levels are `[1, 2, 3, 4, 5]`.
