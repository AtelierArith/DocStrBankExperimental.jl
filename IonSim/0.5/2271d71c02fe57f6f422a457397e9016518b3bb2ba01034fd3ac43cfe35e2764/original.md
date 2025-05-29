```
LinearChain_fromyaml(ions::Vector{<:Ion}, yaml::String; N::Int=10)
```

Load normal mode structure from the specified `yaml` file. It's up to the user to enforce physicality.

```
x:
  - frequency: 1e6
    mode: [0.1, 0.5, 0.3, 0.8]
  - frequency: 2e6
    mode: [0.3, 0.6, 0.5, 3]
y:
  - frequency: 8e6
    mode: [1, 1, 1, 1]
ionpositions: [-1, -0.5, -0.25, 5]
```

It is up to the user to enforce the physicality of this structure.
