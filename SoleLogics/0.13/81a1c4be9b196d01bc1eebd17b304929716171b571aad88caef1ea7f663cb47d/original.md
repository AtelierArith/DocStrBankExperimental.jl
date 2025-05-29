```
struct KripkeStructure{
    FR<:AbstractFrame,
    MAS<:AbstractDict
} <: AbstractKripkeStructure
    frame::FR
    assignment::AS
end
```

Type for representing [Kripke structures](https://en.wikipedia.org/wiki/Kripke_structure_(model_checking)). explicitly; it wraps a `frame`, and an abstract dictionary that assigns an interpretation to each world.
