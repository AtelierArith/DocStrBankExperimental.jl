```
problemset_latex(args...) -> (String,String)
```

Generate the latex source of the problems and solutions.

# Arguments

  * `student_names::AbstractVector{String}`: Students' names
  * `problems::AbstractVector{Function}`: Vector of functions defined using @problem macro
  * `subsets::Union{Pair,Vector{<:Pair}}`: Subset specification or vector of specifications
  * `rng_seed::Integer`: Random number generator's seed to make generated sets repeatable
  * `set_title::String`: Title of the problem set
  * `problem_title::String`: Constant part of the title of individual problems

Subset specifications instructs the function how to pick problems to be assigned to a student from the supplied vector. For example, the specification [1=>1:3, 2=>4:7] will select one out of the first three problems, two out of the problems four to seven and then combine the results. If the ranges overlap, only unique problem numbers are kept.

# Example

```julia-repl
julia> student_names = ["A", "B", "C"];
julia> rng_seed = 123
julia> txt,txt_sol =  problemset_latex(student_names, my_set, 2=>1:3, rng_seed);
julia> write("problems.tex", latex_preamble*txt);
julia> write("solutions.tex", latex_preamble*txt);
```
