```
parse_epanet(path::String)
```

Parses an [EPANET](https://www.epa.gov/water-research/epanet) (.inp) file from the file path `path` and returns a WaterModels data structure (a dictionary of data). See the [OpenWaterAnalytics Wiki](http://wateranalytics.org/EPANET/_inp_file.html) for a thorough description of the EPANET format and its components. Note also that this parsing routine does not necessarily preserve topology nor one-to-one correspondence with the original EPANET model, e.g., each pipe with a valve (check or shutoff) is transformed into a WaterModels pipe component *and* a valve component. Does not perform data correction nor per-unit translations of the data model.
