```julia
struct Model{TimesModelType<:CTModels.AbstractTimesModel, StateModelType<:CTModels.AbstractStateModel, ControlModelType<:CTModels.AbstractControlModel, VariableModelType<:CTModels.AbstractVariableModel, DynamicsModelType<:Function, ObjectiveModelType<:CTModels.AbstractObjectiveModel, ConstraintsModelType<:CTModels.AbstractConstraintsModel} <: CTModels.AbstractModel
```

**Fields**

  * `times::CTModels.AbstractTimesModel`
  * `state::CTModels.AbstractStateModel`
  * `control::CTModels.AbstractControlModel`
  * `variable::CTModels.AbstractVariableModel`
  * `dynamics::Function`
  * `objective::CTModels.AbstractObjectiveModel`
  * `constraints::CTModels.AbstractConstraintsModel`
  * `definition::Expr`
