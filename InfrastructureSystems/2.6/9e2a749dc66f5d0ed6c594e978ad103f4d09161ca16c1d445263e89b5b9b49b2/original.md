```julia
struct FuelCurve{T<:InfrastructureSystems.ValueCurve} <: InfrastructureSystems.ProductionVariableCostCurve{T<:InfrastructureSystems.ValueCurve}
```

  * `value_curve::InfrastructureSystems.ValueCurve`: The underlying `ValueCurve` representation of this `ProductionVariableCostCurve`
  * `power_units::InfrastructureSystems.UnitSystemModule.UnitSystem`: (default: natural units (MW)) The units for the x-axis of the curve
  * `fuel_cost::Union{Float64, InfrastructureSystems.TimeSeriesKey}`: Either a fixed value for fuel cost or the [`TimeSeriesKey`](@ref) to a fuel cost time series
  * `vom_cost::InfrastructureSystems.LinearCurve`: (default of 0) Additional proportional Variable Operation and Maintenance Cost in :/(power_unit h)     represented as a [`LinearCurve`](@ref)

```
FuelCurve(value_curve, power_units, fuel_cost, vom_cost)
FuelCurve(value_curve, fuel_cost)
FuelCurve(value_curve, fuel_cost, vom_cost)
FuelCurve(value_curve, power_units, fuel_cost)
FuelCurve(; value_curve, power_units, fuel_cost, vom_cost)
```

Representation of the variable operation cost of a power plant in terms of fuel (MBTU, liters, m^3, etc.), coupled with a conversion factor between fuel and currency. Composed of a [`ValueCurve`](@ref) that may represent input-output, incremental, or average rate data. The default units for the x-axis are MW and can be specified with `power_units`.
