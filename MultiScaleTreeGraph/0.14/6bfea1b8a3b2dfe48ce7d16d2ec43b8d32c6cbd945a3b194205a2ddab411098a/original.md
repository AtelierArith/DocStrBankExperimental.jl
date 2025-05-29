```
DataFrame(mtg::Node)
DataFrame(mtg::Node, key)
```

Convert an MTG into a DataFrame.

# Arguments

  * `mtg::Node`: An mtg node (usually the root node).
  * `key`: The attribute(s) name(s). Select a list of variables given either as a Symbol

(faster), a String, or an Array of (or a Tuple).

# Examples

```julia
# Importing an mtg from the package:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# Full DataFrame:
DataFrame(mtg)

# Select just :Length:
DataFrame(mtg, :Length)

# Select just :Length and :Width:
DataFrame(mtg, [:Length, :Width])
```
