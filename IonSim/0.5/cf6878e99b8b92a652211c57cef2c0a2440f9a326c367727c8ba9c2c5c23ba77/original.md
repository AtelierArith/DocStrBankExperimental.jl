IonInstance(selected_sublevels::Vector{Tuple}[, manualshift::Dict]) Ion instance of some species

`selected_sublevels` specifies which energy sublevels will be present in the Hilbert space of  this Ion instance, as a subset of all possible sublevels.

Each element of `selected_sublevels` is a 2-element Tuple `(level::String, sublevels)`, with the first element being the name of a level and the second specifying which sublevels should be included. Allowed sublevels are those whose magnetic quantum number `m` is in the set {`-f`, `-f+1`, `-f+2`, ... `f-1`, `f`}, where `f` is the total angular momentum quantum number of `level`. For each `level` specified there are three allowed options to specify the set of `sublevels` to include:

  * `sublevels::Real`: Includes only one `m = sublevels`
  * `sublevels::Vector{Real}`: Includes all sublevels whose magnetic quantum number `m` is in `sublevels`
  * `sublevels = "all"`: Includes all allowed sublevels

If an element of `selected_sublevels` utilizes the first option, specifying a single `m`, one may optionally may this a 3-element tuple instead: `(level::String, m::Real, alias::String)`, assinging this particular sublevel the alias `alias`.

Omission of a level in `selected_sublevels` will exclude all sublevels.

**Fields**

  * `speciesproperties::IonProperties`: Contains constants specifying parameters specific to species
  * `sublevels`::Vector{Tuple{String,Real}}: List of all sublevels present in the Hilbert space
  * `sublevelaliases::Dict{String,Tuple}`: Dict specifying aliases assigned to sublevels, in the format `alias => sublevel`
  * `shape`::Vector{Int}: Dimension of the Hilbert space
  * `manualshift::OrderedDict`: A dictionary with keys denoting the selected levels and values, a real number for describing a shift of the level's energy. This is just a convenient way to add manual shifts to the simulation, such as Stark shifts off of energy levels not present in the Hilbert space, without additional resources
  * `ionnumber`: When the ion is added to an `IonTrap`, this value keeps track of its order
  * `ionposition`: When the ion is added to an `IonTrap`, this value keeps track of its physical position in meters
