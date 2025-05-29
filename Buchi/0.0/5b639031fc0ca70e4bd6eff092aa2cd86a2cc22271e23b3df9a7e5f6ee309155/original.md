APDict{Ta}

While `spot` has words and automata over "conditions", which are Boolean expressions in "atomic propositions", our automata and words are over a type `Ta`. An `APDict{Ta}` establishes a correspondence between `Ta` and binary-encoded Boolean expressions.

`APDict{Ta}` is an abstract type, that supplies methods

  * `bdd_dict(::APDict)` for access to an underlying dictionary of boolean decision diagrams
  * `getindex(::APDict,::Ta)` to obtain a corresponding `BDD`
  * `(::APDict)(::BDD)` to obtain a corresponding `Ta`
  * `get_aut(::APDict)` to access an underlying automaton, only used to register atomic propositions
  * `get_factory(::APDict)` to access, if it exists, an `APDictFactory` that produces dictionaries for tuples.
