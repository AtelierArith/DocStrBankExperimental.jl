```
ReserveRequirement <: Modification
```

Representation of reserve requirement, such that the sum of eligible power injection capacity in the region (including both generators and storage devices) is constrained to be greater than or equal to some percentage above the load.

Keyword arguments:

  * `name` - name of the modification
  * `area` - the area by which to group the buses by for the reserve requirements.
  * `credit_gen` - the [`Crediting`](@ref) for the generators, defaults to [`AvailabilityFactorCrediting`](@ref)
  * `credit_stor` - the [`Crediting`](@ref) for the storage facilities (see [`Storage`](@ref)), defaults to [`StandardStorageReserveCrediting`](@ref)
  * `requirements_file` - a table with the subareas and the percent requirement of power capacity above the load.  See [`summarize_table(::Val{:reserve_requirements})`](@ref)
  * `flow_limits_file` - (optional) a table with positive and negative flow limits from each subarea to each other subarea.  See [`summarize_table(::Val{:reserve_flow_limits})`](@ref).  If none provided, it is assumed that no flow is permitted between regions.
  * `load_type` - a `String` for what type of load to base the requirement off of.  Can be either: 

      * `plnom` - (default), nominal load power.
      * `plserv` - served load power.

Model Modification:

  * Variables

      * `pres_flow_<name>` - (nflow x nyr x nhr) Reserve power flow for each row of the flow limit table, bounded by forward and reverse max flows. (only present if there is `flow_limits_file` file provided)
  * Expressions

      * `pres_total_subarea_<name>` - (nsubarea x nyr x nhr) Reserve power from all sources for each subarea
      * `pres_gen_subarea_<name>` - (nsubarea x nyr x nhr) Reserve power from generators for each subarea (function of capacity)
      * `pres_stor_subarea_<name>` - (nsubarea x nyr x nhr) Reserve power from storage units (only present if there is [`Storage`](@ref) in the model.)
      * `pres_req_subarea_<name>` - (nsubarea x nyr x nhr) Required reserve power (function of load), depends on `requirements_file` and `load_type`
      * `pres_flow_subarea_<name>` - (nsubarea x nyr x nhr) Reserve flow flowing out of each subarea, function of `pres_flow_<name>` variable.   (only present if there is `flow_limits_file` file provided)
  * Constraints

      * `cons_pres_<name>` - (nsubarea x nyr x nhr) Constrain that `pres_total_subarea_<name> ≥ pres_req_subarea_<name>`.

Adds results:

  * `(:gen, :<name>_rebate)` - the total rebate for generators, for satisfying the reserve requirement.  Generally ≥ 0.  This is added to `(:gen, :net_total_revenue_prelim)`, and subtracted from electricity `user` welfare.
  * `(:storage, :<name>_rebate)` - (only added if [`Storage`](@ref) included) the total rebate for storage units, for satisfying the reserve requirement.  Generally ≥ 0.  This is added to `(:storage, :net_total_revenue_prelim)`, and subtracted from electricity `user` welfare.
