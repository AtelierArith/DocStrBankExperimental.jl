```
apes(echogram, model, solver[; params, result_handler, safe_precision, distributed])
```

Run the automatic probabilistic echo solver defined by the inverse `model` and  solution method `solver` on the acoustic backstter data in `echogram`.

# Arguments

  * `echogram::DimArray`: Acoustic backscatter data in the linear domain (i.e.,   volume backsattering coefficient $s_v$, area backsattering coefficient $s_a$,   or nautical area scattering coefficient, $NASC$). The last dimension of    the `DimArray` should be named `:F` and index the acoustic frequencies;    all other dimensions should reference spatial/temporal coordinates.
  * `model::Function`: Probabilistic inverse model defined with Turing.jl   or DynamicPPL.jl. This model should have the signature `model(data, params)`,   where `data` and `params` contain the acoustic data and any additional   parameters. See below for more details.
  * `solver::AbstractSolver`: The method used to solve the inverse problem   specified in `model`. See `MCMCSolver` and `MAPSolver` for more detail.
  * `params`: Optional additional params to pass to `model`.
  * `result_handler`: Optional function to transform the output of the solver    before (for instance, by calculating the means of a Markov chain).
  * `distributed::Bool=false`: Whether to use all available processors when    fitting model to echogram cells.

# Details

This function applies a probabilistic inverse backscattering model defined using Turing.jl to each spectrum in a mulifrequency echogram. The model's constructor must accept two arguments:

  * `data`: A `NamedTuple` or other structure accessible by dot-notation, with   fields `coords`, `freqs`, and `backscatter`. These contain the observed   acoustic data. The model doesn't have to use all of them.
  * `params`: Optional `NamedTuple` or other object, containing any constants or   auxiliary information used by the model.
