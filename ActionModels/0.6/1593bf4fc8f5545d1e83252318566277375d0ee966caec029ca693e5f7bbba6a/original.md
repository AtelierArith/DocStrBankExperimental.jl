```
premade_agent(model_name::String, config::Dict = Dict(); verbose::Bool = true)
```

Create an agent from the list of premade agents.

# Arguments

  * 'model_name::String': Name of the premade model. Returns a list of possible model names if set to 'help'.
  * 'config::Dict = Dict()': A dictionary with configurations for the agent, like parameters and settings.
  * 'verbose::Bool = true': If set to false, warnings are hidden.
