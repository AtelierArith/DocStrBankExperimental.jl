```
mutable struct Nullable{T} <: AbstractNullable{T}
```

Foreign Key model field

The foreign key field can be constructed with the T element or with nothing. The `loaded` field is used in the lazy loading of the foreign element. When the foreign element is loaded the `loaded` attributed is set to true

```
struct ModelA <: Model ... end
struct ModelB <: Model
    ...
    foreign_field::ForeignKey{ModelA}
end
```
