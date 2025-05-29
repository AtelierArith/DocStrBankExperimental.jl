```
GeneticSearchIterator{FitnessFunction,CrossOverFunction,MutationFunction,SelectParentsFunction,EvaluationFunction} <: ProgramIterator
```

Defines an [`ProgramIterator`](@ref) using genetic search. 

Consists of:

  * `examples::Vector{<:IOExample}`: a collection of examples defining the specification
  * `evaluation_function::EvaluationFunction`: interpreter to evaluate the individual programs
  * `population_size::Int64`: number of inviduals in the population
  * `mutation_probability::Float64`: probability of mutation for each individual
  * `maximum_initial_population_depth::Int64`: maximum depth of trees when population is initialized

end
