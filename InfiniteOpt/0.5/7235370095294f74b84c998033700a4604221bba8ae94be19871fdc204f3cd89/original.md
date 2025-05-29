```
FunctionalDiscreteMeasureData{P <: Union{JuMP.AbstractVariableRef,
                              Vector{<:JuMP.AbstractVariableRef}},
                              B <: Union{Float64, Vector{Float64}},
                              I <: AbstractGenerativeInfo,
                              F1 <: Function,
                              F2 <: Function
                              } <: AbstractMeasureData
```

A DataType for mutable measure abstraction data where the abstraction is of the form: $measure = \int_{\tau \in T} f(\tau) w(\tau) d\tau \approx \sum_{i = 1}^N \alpha_i f(\tau_i) w(\tau_i)$. This abstraction is equivalent to that of [`DiscreteMeasureData`](@ref), but the difference is that the supports are not fully known at the time of measure creation. Thus, functions are stored that will be used to generate the concrete support points $\tau_i$ and their coefficients $\alpha_i$ when the measure is evaluated (expanded). These supports are identified/generated in accordance with the `label` with a gaurantee that at least `num_supports` are generated. For example, if `label = MCSample` and `num_supports = 100` then the measure will use all of the supports stored in the `parameter_refs` with the label `MCSample` and will ensure there are at least 100 are generated. This type can be used for both 1-dimensional and multi-dimensional measures.

For 1-dimensional measures over independent infinite parameters, the  `generative_supp_info` specifies the info needed to make generative supports based  on those with that exist with `label`. Note that only 1 kind of generative  supports are allowed for each infinite parameter.

**Fields**

  * `parameter_refs::P`: The infinite parameter(s) over which the integration occurs.                    These can be comprised of multiple independent parameters,                    but dependent parameters cannot be mixed with other types.
  * `coeff_function::F1`: Coefficient generation function making $\alpha_i$                             for the above measure abstraction. It should take                             all the supports as input (formatted as an Array)                             and return the corresponding vector of coefficients.
  * `min_num_supports::Int`: Specifies the minimum number of supports $\tau_i$                      desired in association with `parameter_refs` and `label`.
  * `label::DataType`: Label for the support points $\tau_i$ which are/will be                  stored in the infinite parameter(s), stemming from [`AbstractSupportLabel`](@ref).
  * `generative_supp_info::I`: Information needed to generate supports based on other   existing ones.
  * `weight_function::F2`: Weighting function $w$ must map an individual                             support value to a `Real` scalar value.
  * `lower_bounds::B`: Lower bounds in accordance with $T$, this denotes the                 intended interval of the measure and should be `NaN` if ignored
  * `upper_bounds::B`: Same as above but the upper bounds.
  * `is_expect::Bool`: Is this data associated with an expectation call?
