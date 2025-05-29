```julia
struct Poisson{Form, S} <: Cthonios.AbstractPhysics{1, 0, 0}
```

  * `formulation::Any`
  * `laplacian::Cthonios.Laplacian{1}`
  * `source::Any`

# TODO ソース項カーネルを作成する
