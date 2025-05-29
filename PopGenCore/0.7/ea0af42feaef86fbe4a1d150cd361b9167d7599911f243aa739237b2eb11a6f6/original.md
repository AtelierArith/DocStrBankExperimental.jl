```
# Replace by matching
populations!(data::PopData, rename::Dict)
populations!(data::PopData, rename::Vector{String})
populations!(data::PopData, samples::Vector{String}, populations::Vector{String})
```

Multiple methods to rename or reassign population names to a `PopData`.

## Rename using a Dictionary

Rename existing population ID's of `PopData` using a `Dict` of `population_name => replacement`

**Example**

```
potatopops = Dict("1" => "Idaho", "2" => "Russet")
populations!(potatoes, potatopops)
```

## Rename using a Vector of Strings

If the number of new names is equal to the number of current unique population names, the method will rename the existing populations in the order with which they appear  via `unique()`. If the number of new population names is equal to the number of samples, the method will instead assign new population names to every sample in the order with which they appear in `sampleinfo(popdata)`.

**Example**

```
# rename (2) existing populations
potatopops = ["Idaho", "Russet"]
populations!(potatoes, potatopops)

# assign new names to all [44] samples
potatopops = repeat(["Idaho", "Russet"], inner = 22) ;
populations!(potatoes, potatopops)
```

## Reassign using samples and new population assignments

Completely reassign populations for each individual. Takes two vectors of strings as input: one of the sample names, and the other with their new corresponding population name. This can be useful to change population names for only some individuals.

**Example**

```
populations!(potatoes, ["potato_1", "potato_2"], ["north", "south"])
```
