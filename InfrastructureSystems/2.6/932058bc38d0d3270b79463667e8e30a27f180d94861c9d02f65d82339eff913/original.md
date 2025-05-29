```julia
struct CostCurve{T<:InfrastructureSystems.ValueCurve} <: InfrastructureSystems.ProductionVariableCostCurve{T<:InfrastructureSystems.ValueCurve}
```

  * `value_curve::InfrastructureSystems.ValueCurve`: The underlying `ValueCurve` representation of this `ProductionVariableCostCurve`
  * `power_units::InfrastructureSystems.UnitSystemModule.UnitSystem`: (default: natural units (MW)) The units for the x-axis of the curve
  * `vom_cost::InfrastructureSystems.LinearCurve`: (default of 0) Additional proportional Variable Operation and Maintenance Cost in     :/(power_unit h), represented as a [`LinearCurve`](@ref)

```
CostCurve(value_curve, power_units, vom_cost)
CostCurve(; value_curve, power_units, vom_cost)
```

Direct representation of the variable operation cost of a power plant in currency. Composed of a [`ValueCurve`](@ref) that may represent input-output, incremental, or average rate data. The default units for the x-axis are MW and can be specified with `power_units`.
