```
LaSROptions(;kws...) <: SymbolicRegression.AbstractOptions
```

Construct options for `equation_search` and other functions. Also read: SymbolicRegression.Options

# Arguments

  * `use_llm::Bool`: Whether to use LLM inference. (default: false)
  * `use_concepts::Bool`: Whether to summarize candidate programs into natural-language concepts and use those concepts to guide the search (i.e., a specialization of FunSearch). (default: false)   NOTE: If `use_llm` is false, then `use_concepts` is ignored.
  * `use_concept_evolution::Bool`: Whether to evolve the concepts after every iteration. (default: false)   NOTE: If `use_concepts` is false, then `use_concept_evolution` is ignored.
  * `mutation_weights::LaSRMutationWeights`: Unnormalized mutation weights for the mutation operators (e.g., `llm_mutate`, `llm_randomize`).
  * `llm_operation_weights::LLMOperationWeights`: Normalized probabilities of using LLM-based crossover vs. symbolic crossover.
  * `num_pareto_context::Int64`: Number of equations to sample from the Pareto frontier for summarization.
  * `num_generated_equations::Int64`: Number of new equations to generate from the LLM per iteration.
  * `num_generated_concepts::Int64`: Number of new concepts to generate from the LLM per iteration.
  * `num_concept_crossover::Int64`: Number of concepts to add for concept crossover. (default: 2)
  * `max_concepts::UInt32`: Maximum number of concepts to retain in the concept library. (default: 30)
  * `is_parametric::Bool`: A special flag to allow sampling parametric equations from LaSR. (default: false)
  * `llm_context::AbstractString`: A natural-language hint or context string passed to the LLM.
  * `variable_names::Union{Dict,Nothing}`: A mapping of symbolic variable names to domain-meaningful names. (default: nothing)
  * `prompts_dir::AbstractString`: The location of zero-shot prompts for the LLM. Specialize these prompts to your domain for better performance. (default: "prompts/")
  * `idea_database::Vector{AbstractString}`: A list of natural-language concept “ideas” for seeding the LLM. (default: [])
  * `api_key::AbstractString`: An API key for an OpenAI-compatible server. Required.
  * `model::AbstractString`: The LLM model name for the OpenAI-compatible server. Required.
  * `api_kwargs::Dict`: Additional keyword arguments for the LLM's API. Must include `url::AbstractString` to specify the endpoint. (default: `Dict("url" => "...")`)

      * For example: `Dict("url" => "http://localhost:11440/v1", "max_tokens" => 1000)`
  * `http_kwargs::Dict`: Additional keyword arguments for HTTP requests.

      * `retries::Int`: Number of retries. (default: 3)
      * `readtimeout::Int`: Read timeout in seconds. (default: 3600)
  * `verbose::Bool`: Whether to print tokens and additional debugging info for each LLM call. (default: true)
