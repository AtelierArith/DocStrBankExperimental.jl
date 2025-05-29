```
SSD_examples::Dict{Symbol,String}
```

Dictionary with the paths to the example detector configuration files provided by the package.

Find the possible keys of the dictionary with `keys(SSD_examples)`.

The example detector configuration files can be loaded via

```
path_to_config_file = SSD_examples[:InvertedCoax]
sim = Simulation(path_to_config_file)
```
