```
InputData(name::Symbol, option::Symbol, data::Any)
```

Represents a more structured block of input data. e.g. `InputData(:k_points, :automatic, (6,6,6,1,1,1))` would be translated for a QE calculation into

```
K_POINTS(automatic)
6 6 6 1 1 1
```
