```
aiclassify(prompt_schema::AbstractOpenAISchema, prompt::ALLOWED_PROMPT_TYPE;
    choices::AbstractVector{T} = ["true", "false", "unknown"],
    model::AbstractString = MODEL_CHAT,
    api_kwargs::NamedTuple = NamedTuple(),
    token_ids_map::Union{Nothing, Dict{<:AbstractString, <:Integer}} = nothing,
    kwargs...) where {T <: Union{AbstractString, Tuple{<:AbstractString, <:AbstractString}}}
```

Classifies the given prompt/statement into an arbitrary list of `choices`, which must be only the choices (vector of strings) or choices and descriptions are provided (vector of tuples, ie, `("choice","description")`).

It's quick and easy option for "routing" and similar use cases, as it exploits the logit bias trick and outputs only 1 token. classify into an arbitrary list of categories (including with descriptions). It's quick and easy option for "routing" and similar use cases, as it exploits the logit bias trick, so it outputs only 1 token.

!!! Note: The prompt/AITemplate must have a placeholder `choices` (ie, `{{choices}}`) that will be replaced with the encoded choices

Choices are rewritten into an enumerated list and mapped to a few known OpenAI tokens (maximum of 40 choices supported). Mapping of token IDs for GPT3.5/4 are saved in variable `OPENAI_TOKEN_IDS`.

It uses Logit bias trick and limits the output to 1 token to force the model to output only true/false/unknown. Credit for the idea goes to [AAAzzam](https://twitter.com/AAAzzam/status/1669753721574633473).

# Arguments

  * `prompt_schema::AbstractOpenAISchema`: The schema for the prompt.
  * `prompt`: The prompt/statement to classify if it's a `String`. If it's a `Symbol`, it is expanded as a template via `render(schema,template)`. Eg, templates `:JudgeIsItTrue` or `:InputClassifier`
  * `choices::AbstractVector{T}`: The choices to be classified into. It can be a vector of strings or a vector of tuples, where the first element is the choice and the second is the description.
  * `model::AbstractString = MODEL_CHAT`: The model to use for classification. Can be an alias corresponding to a model ID defined in `MODEL_ALIASES`.
  * `api_kwargs::NamedTuple = NamedTuple()`: Additional keyword arguments for the API call.
  * `token_ids_map::Union{Nothing, Dict{<:AbstractString, <:Integer}} = nothing`: A dictionary mapping custom token IDs to their corresponding integer values. If `nothing`, it will use the default token IDs for the given model.
  * `kwargs`: Additional keyword arguments for the prompt template.

# Example

Given a user input, pick one of the two provided categories:

```julia
choices = ["animal", "plant"]
input = "Palm tree"
aiclassify(:InputClassifier; choices, input)
```

Choices with descriptions provided as tuples:

```julia
choices = [("A", "any animal or creature"), ("P", "any plant or tree"), ("O", "anything else")]

# try the below inputs:
input = "spider" # -> returns "A" for any animal or creature
input = "daphodil" # -> returns "P" for any plant or tree
input = "castle" # -> returns "O" for everything else
aiclassify(:InputClassifier; choices, input)
```

You could also use this function for routing questions to different endpoints (notice the different template and placeholder used), eg, 

```julia
choices = [("A", "any question about animal or creature"), ("P", "any question about plant or tree"), ("O", "anything else")]
question = "how many spiders are there?"
msg = aiclassify(:QuestionRouter; choices, question)
# "A"
```

You can still use a simple true/false classification:

```julia
aiclassify("Is two plus two four?") # true
aiclassify("Is two plus three a vegetable on Mars?") # false
```

`aiclassify` returns only true/false/unknown. It's easy to get the proper `Bool` output type out with `tryparse`, eg,

```julia
tryparse(Bool, aiclassify("Is two plus two four?")) isa Bool # true
```

Output of type `Nothing` marks that the model couldn't classify the statement as true/false.

Ideally, we would like to re-use some helpful system prompt to get more accurate responses. For this reason we have templates, eg, `:JudgeIsItTrue`. By specifying the template, we can provide our statement as the expected variable (`it` in this case) See that the model now correctly classifies the statement as "unknown".

```julia
aiclassify(:JudgeIsItTrue; it = "Is two plus three a vegetable on Mars?") # unknown
```

For better results, use higher quality models like gpt4, eg, 

```julia
aiclassify(:JudgeIsItTrue;
    it = "If I had two apples and I got three more, I have five apples now.",
    model = "gpt4") # true
```
