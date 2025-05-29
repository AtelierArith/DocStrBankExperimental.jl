```
VariableReaction(VT, localname => link_namestr, units, description; attributes=Tuple()) -> VariableReaction{VT}
VariableReaction(VT, linklocal_namestr, units, description; attributes=Tuple()) -> VariableReaction{VT}    

VarProp, VarPropScalar, VarPropStateIndep, VarPropScalarStateIndep -> VariableReaction{VT_ReactProperty}
VarDep, VarDepColumn, VarDepScalar, VarDepStateIndep, VarDepColumnStateIndep, VarDepScalarStateIndep -> VariableReaction{VT_ReactDependency}
VarTarget, VarTargetScalar -> VariableReaction{VT_ReactTarget}
VarContrib, VarContribColumn, VarContribScalar -> VariableReaction{VT_ReactContributor}
VarStateExplicit, VarStateExplicitScalar -> VariableReaction{VT_ReactDependency}
VarDeriv, VarDerivScalar -> VariableReaction{VT_ReactContributor}
VarState, VarStateScalar -> VariableReaction{VT_ReactDependency}
VarConstraint, VarConstraintScalar -> VariableReaction{VT_ReactDependency}

[deprecated] VariableReaction(VT, localname, units, description; link_namestr, attributes=Tuple()) -> VariableReaction{VT}
```

Reaction view on a model variable.

Reactions define [`AbstractVarList`](@ref)s of `VariableReaction`s when creating a [`ReactionMethod`](@ref).  Within a `ReactionMethod`, a `VariableReaction` is referred to by `localname`. When the model is initialised,  [`VariableDomain`](@ref) variables are created that link together `VariableReaction`s with the same `link_namestr`, and data Arrays are allocated. `views` on the `VariableDomain` data Arrays are then passed to the [`ReactionMethod`](@ref) function at each timestep.

# Subtypes

The Type parameter `VT` is one of `VT_ReactProperty`, `VT_ReactDependency`, `VT_ReactContributor`, `VT_ReactTarget`, where  short names are defined for convenience:

```
const VarPropT        = VariableReaction{VT_ReactProperty}
const VarDepT         = VariableReaction{VT_ReactDependency}
const VarTargetT      = VariableReaction{VT_ReactTarget}
const VarContribT     = VariableReaction{VT_ReactContributor}
```

There are two pairings of `VariableReaction`s with [`VariableDomain`](@ref)s:

  * Reaction Property and Dependency Variables, linked to a [`VariableDomPropDep`](@ref). These are used to represent   a quantity calculated in one Reaction that is then used by other Reactions.
  * Reaction Target and Contributor Variables, linked to a [`VariableDomContribTarget`](@ref). These are used to represent   a flux-like quantity, with one Reaction definining the Target and multiple Reactions adding contributions.

# Variable Attributes and constructor convenience functions

Variable attributes are used to define Variable `:space` [`AbstractSpace`](@ref) (scalar, per-cell, etc) and data content `:field_data` [`AbstractData`](@ref),  and to label state Variables for use by numerical solvers. 

`VariableReaction` is usually not called directly, instead convenience functions are defined that provide commonly-used combinations of `VT` and `attributes`:

|                short name |                    VT |    attributes |                 |                    |                       |             |                |
| -------------------------:| ---------------------:| -------------:| ---------------:| ------------------:| ---------------------:| -----------:| --------------:|
|                           |                       |      `:space` |   `:field_data` |       `:vfunction` | `:initialize_to_zero` | `:datatype` | `:is_constant` |
|                           |                       |               |                 |                    |                       |             |                |
|                 `VarProp` |    `VT_ReactProperty` |   `CellSpace` |    `ScalarData` |     `VF_Undefined` |                     - |           - |          false |
|           `VarPropScalar` |    `VT_ReactProperty` | `ScalarSpace` |    `ScalarData` |     `VF_Undefined` |                     - |           - |          false |
|       `VarPropStateIndep` |    `VT_ReactProperty` |   `CellSpace` |    `ScalarData` |     `VF_Undefined` |                     - |   `Float64` |           true |
| `VarPropScalarStateIndep` |    `VT_ReactProperty` | `ScalarSpace` |    `ScalarData` |     `VF_Undefined` |                     - |   `Float64` |           true |
|                           |                       |               |                 |                    |                       |             |                |
|                  `VarDep` |  `VT_ReactDependency` |   `CellSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|            `VarDepColumn` |  `VT_ReactDependency` | `ColumnSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|            `VarDepScalar` |  `VT_ReactDependency` | `ScalarSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|        `VarDepStateIndep` |  `VT_ReactDependency` |   `CellSpace` | `UndefinedData` |     `VF_Undefined` |                     - |   `Float64` |           true |
|  `VarDepColumnStateIndep` |  `VT_ReactDependency` | `ColumnSpace` | `UndefinedData` |     `VF_Undefined` |                     - |   `Float64` |           true |
|  `VarDepScalarStateIndep` |  `VT_ReactDependency` | `ScalarSpace` | `UndefinedData` |     `VF_Undefined` |                     - |   `Float64` |           true |
|                           |                       |               |                 |                    |                       |             |                |
|               `VarTarget` |      `VT_ReactTarget` |   `CellSpace` |    `ScalarData` |     `VF_Undefined` |                `true` |           - |          false |
|         `VarTargetScalar` |      `VT_ReactTarget` | `ScalarSpace` |    `ScalarData` |     `VF_Undefined` |                `true` |           - |          false |
|                           |                       |               |                 |                    |                       |             |                |
|              `VarContrib` | `VT_ReactContributor` |   `CellSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|        `VarContribColumn` | `VT_ReactContributor` | `ColumnSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|        `VarContribScalar` | `VT_ReactContributor` | `ScalarSpace` | `UndefinedData` |     `VF_Undefined` |                     - |           - |          false |
|                           |                       |               |                 |                    |                       |             |                |
|        `VarStateExplicit` |  `VT_ReactDependency` |   `CellSpace` |    `ScalarData` | `VF_StateExplicit` |                     - |           - |          false |
|  `VarStateExplicitScalar` |  `VT_ReactDependency` | `ScalarSpace` |    `ScalarData` | `VF_StateExplicit` |                     - |           - |          false |
|                `VarDeriv` | `VT_ReactContributor` |   `CellSpace` |    `ScalarData` |         `VF_Deriv` |                `true` |           - |          false |
|          `VarDerivScalar` | `VT_ReactContributor` | `ScalarSpace` |    `ScalarData` |         `VF_Deriv` |                `true` |           - |          false |
|                           |                       |               |                 |                    |                       |             |                |
|                `VarState` |  `VT_ReactDependency` |   `CellSpace` |    `ScalarData` |         `VF_State` |                     - |           - |          false |
|          `VarStateScalar` |  `VT_ReactDependency` | `ScalarSpace` |    `ScalarData` |         `VF_State` |                     - |           - |          false |
|           `VarConstraint` | `VT_ReactContributor` |   `CellSpace` |    `ScalarData` |    `VF_Constraint` |                `true` |           - |          false |
|     `VarConstraintScalar` | `VT_ReactContributor` | `ScalarSpace` |    `ScalarData` |    `VF_Constraint` |                `true` |           - |          false |

This illustrates some general principles for the use of attributes:

  * All Variables must define the `:space` VariableAttribute (a subtype of [`AbstractSpace`](@ref)) to specify whether they are Domain scalars, per-cell quantities, etc. This is used to define array dimensions, and to check that dimensions match when variables are linked.
  * The `:field_data` attribute (a subtype of [`AbstractData`](@ref)) specifies the quantity that Property and Target Variables represent. This defaults to  `ScalarData` to represent a scalar value. To eg represent a single isotope the `:field_data` attribute should be set to `IsotopeLinear`. Dependency and Contributor Variables with `:field_data = UndefinedData` then acquire this value when they are linked, or may specify `:field_data` to constrain allowed links.
  * The `:initialize_to_zero` attribute is set for Target variables, this is than used (by the ReactionMethod created by [`add_method_initialize_zero_vars_default!`](@ref)) to identify variables that should be initialised to zero at the start of each timestep.
  * The `:vfunction` attribute is used to label state Variables and corresponding time derivatives, for access by a numerical solver.

      * An ODE-like combination of a state variable and time derivative are defined by a paired `VarStateExplicit` and `VarDeriv`. Note that that these are just `VarDep` and `VarContrib` with the `:vfunction` attribute set, and that there is no `VarProp` and `VarTarget` defined in the model (these are effectively provided by the numerical solver). The pairing is defined by the naming convention of `varname` and `varname_sms`.
      * An algebraic constraint (for a DAE) is defined by a `VarState` and `VarConstraint`. Note that that these are just `VarDep` and `VarContrib` with the `:vfunction` attribute set, and that there is no `VarProp` and `VarTarget` defined in the model (these are effectively provided by the numerical solver). These variables are not paired.
      * The :initialize*to*zero attribute is also set for Contributor variables VarDeriv and VarConstraint (as there is no corresponding Target variable in the model).
      * The :field_data attribute should be set on labelled state etc Variables (as there are no corresponding Property or Target variables in the model to define this).
  * The `:is_constant` attribute is used to identify constant Property Variables (not modified after initialisation). A Dependency Variable with :is_constant = true can only link to a constant Property Variable.
  * The `:datatype` attribute is used both to provide a concrete datatype for constant Variables, and to exclude a non-constant Variable from automatic differentiation (TODO document that usage).

Additional attributes can be specified to provide model-specific information, with defaults defined in the Reaction .jl code that can often then be overridden in the .yaml configuration file, see [`StandardAttributes`](@ref). Examples include:

  * `:initial_value`, `:norm_value`, `:initial_delta` for state variables or constant variables. NB: the Reaction creating these variables is responsible for implementing a setup method to read the attributes and set the variable data array appropriately at model initialisation.
  * An `:advect` attribute is used to label tracer variables to indicate that they should have advective transport applied by a transport Reaction included in the model.

NB: after Variables are linked to Domain Variables, the attributes used are those from the `master` Variable (either a Property or Target variable, or a labelled state variable Dependency or Contributor with no corresponding Property or Target). Additional attributes must therefore be set on this master Variable.

# Specifying links

`localname` identifies the `VariableReaction` within the `Reaction`, and can be used to set `variable_attributes:` and `variable_links:` in the .yaml configuration file.

`linkreq_domain.linkreq_subdomain.linkreq_name` defines the Domain, Subdomain and name for run-time linking to [`VariableDomain`](@ref) variables. 

# Arguments

  * `VT::VariableType`:  one of `VT_ReactProperty`, `VT_ReactDependency`, `VT_ReactContributor`, `VT_ReactTarget`
  * `localname::AbstractString`: Reaction-local Variable name
  * `link_namestr::AbstractString`: `<linkreq_domain>.[linkreq_subdomain.]linkreq_name`. Parsed by [`parse_variablereaction_namestr`](@ref) to define the requested linking to `Domain` Variable.
  * `linklocal_namestr::AbstractString`:  `<linkreq_domain>.[linkreq_subdomain.]localname`. Convenience form to define both `localname` and requested linking to Domain Variable, for the common case where `linkreq_name == localname`.
  * `units::AbstractString`: units ("" if not applicable)
  * `description::AbstractString`: text describing the variable

# Keywords

  * `attributes::Tuple(:attrb1name=>attrb1value, :attrb2name=>attrb2value, ...)`:  variable attributes, see [`StandardAttributes`](@ref), [`set_attribute!`](@ref), [`get_attribute`](@ref)
