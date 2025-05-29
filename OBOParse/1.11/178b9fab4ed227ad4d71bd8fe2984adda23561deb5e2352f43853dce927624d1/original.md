Ontology term.

The `Term` object is a node in the direct acyclic ontology graph. Its outgoing and incoming edges represent the relations with the other nodes and could be retrieved by

```julia
relationship(term, sym)
```

and

```julia
rev_relationship(term, sym)
```

respectively, where `sym` is the relationship annotation (e.g. `:part_of`, `:is_a`, `:regulates`).
