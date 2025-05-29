```
HydrogenStorage{T} <: AbstractH2Storage{T}
```

`Storage` node in which the maximum discharge usage is directly linked to the charge capacity, that is it is not possbible to have a larger discharge usage than the charge capacity and a multiplier `discharge_charge`.

It differs from [`SimpleHydrogenStorage`](@ref) through incorporation of a piecewise linear curve for the electricity demand, depending on the current storage level and the defined upper (field `p_max`) and charge pressure (field `p_charge`) of the node.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`charge::EMB.UnionCapacity`** are the charging parameters of the `SimpleHydrogenStorage` node. Depending on the chosen type, the charge parameters can include variable OPEX, fixed OPEX, and/or a capacity.
  * **`stor_res::Resource`** is the stored [`Resource`](@extref EnergyModelsBase.Resource).
  * **`el_res::Resource`** is the [`Resource`](@extref EnergyModelsBase.Resource) representing electricity. It **must** be specified explicitly for the proper calculation of the electricity demand for compression.
  * **`data::Vector{<:Data}`** is the additional data (*e.g.*, for investments). The field `data` is conditional through usage of a constructor.
  * **`discharge_charge::Float64`** is the multiplier for specifying the maximum discharge rate relative to the charge rate. A value of `2.0` would imply that it is possible to have double the discharge rate compared to the installed charge capacity.
  * **`level_charge::Float64`** is the multiplier for specifying the installed storage level capacity relative to the installed storage charge capacity. It is used for checking input data in the case of a generic model and for limiting investments in the case of an [`AbstractInvestmentModel`](@extref EnergyModelsBase.AbstractInvestmentModel).
  * **`p_min::Float64`** is the minimum pressure in the storage.
  * **`p_charge::Float64`** is the charging pressure into the storage.
  * **`p_max::Float64`** is the maximum pressure in the storage.

!!! warning "Units for pressure"
    The unit for the pressure inputs `p_min`, `p_charge`, and `p_max` are not relevant as the isentropic compression is only dependent on the pressure ratio. It is however necessary that all pressures use the same unit, *e.g.*, bar or Pa.

