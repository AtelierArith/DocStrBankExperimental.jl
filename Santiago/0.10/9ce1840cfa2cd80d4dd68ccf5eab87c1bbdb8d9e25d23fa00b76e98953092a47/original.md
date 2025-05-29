Represents a santiation system.

Has the following fields:

  * `techs::Set{Santiago.AbstractTech}`
  * `connections::Set{Tuple{Santiago.Product, Santiago.AbstractTech, Santiago.AbstractTech}}`
  * `complete::Bool`
  * `properties::Dict`
