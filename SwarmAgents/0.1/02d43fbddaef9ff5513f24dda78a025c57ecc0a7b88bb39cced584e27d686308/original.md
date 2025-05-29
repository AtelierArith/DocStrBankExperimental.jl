```
Agent
```

Agent is a stateless struct that holds the the reference to LLM, tools and the instructions.

# Fields

  * `name::String`: The name of the agent.
  * `model::String`: The model to use for the agent.
  * `instructions::String`: The instructions for the agent.
  * `tool_map::Dict{String, AbstractTool}`: A dictionary of tools available to the agent.
  * `tool_choice::Union{String, Nothing}`: The tool choice for the agent.
  * `parallel_tool_calls::Bool`: Whether to allow parallel tool calls. Defaults to `true` - NOT SUPPORTED YET.
