```
translate(model::AbstractLLM, description::AbstractString; interactive::Bool = false)
```

Translate the natural-language `description` of an optimization problem into a Constraint Programming model by querying the Large Language Model `model`. If `interactive`, the user will be prompted via the command line to inspect the intermediate outputs of the LLM, and possibly modify them.
