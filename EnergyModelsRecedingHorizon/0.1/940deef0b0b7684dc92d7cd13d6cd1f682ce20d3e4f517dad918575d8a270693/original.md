```
struct ElementValue{T<:Union{TimeProfile, Real}}
```

An `ElementValue` represents an instance of a given [`AbstractElement`](@extref EnergyModelsBase.AbstractElement) with an assigned value. It replaces dictionaries in which an `AbstractElement` is used as key value so that it is possible to reset the `AbstractElement`

## Fields

  * **`element::N`** is the instance of the element.
  * **`value::T`** is the used value.
