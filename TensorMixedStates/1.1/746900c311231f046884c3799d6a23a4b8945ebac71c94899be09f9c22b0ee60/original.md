```
output(::Simulation, [ filename => measure1, ... ])
```

compute the given measurements on a simultation and output them to the associated file or dict

filenames are interpreted by get_sim_file (see there for special values)

# Examples

```
output(sim, "file" => [X, X(1)Y(2), (X, Y)])
output(sim, [ "file1" => [X, Y(2)], "file2" => Trace])
```
