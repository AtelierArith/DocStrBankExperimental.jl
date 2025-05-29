```
apply_schema(t::AbstractTerm, schema::StatsModels.FullRank, Mod::Type)
```

Apply a schema, under the assumption that when a less-than-full rank model matrix would be produced, categorical terms should be "promoted" to full rank (where a categorical variable with $k$ levels would produce $k$ columns, instead of $k-1$ in the standard contrast coding schemes).  This step is applied automatically when `Mod <: StatisticalModel`, but other types of models can opt-in by adding a method like

```
StatsModels.apply_schema(t::FormulaTerm, schema::StatsModels.Schema, Mod::Type{<:MyModelType}) =
    apply_schema(t, StatsModels.FullRank(schema), mod)
```

See the section on [Modeling categorical data](@ref) in the docs for more information on how promotion of categorical variables works.
