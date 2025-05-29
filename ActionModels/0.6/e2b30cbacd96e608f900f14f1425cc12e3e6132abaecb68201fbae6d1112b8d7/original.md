```
init_agent(action_model::Function; substruct::Any = nothing, parameters::Dict = Dict(), states::Union{Dict, Vector} = Dict(),
settings::Dict = Dict(), parameter_groups::Dict = Dict())
```

Initialize an agent. 

Note that action*model can also be specified as a vector of action models: action*model::Vector{Function}. In this case the action models will be stored in the agent's settings. In that case use the function 'multiple_actions'

# Arguments

  * 'action_model::Function': a function specifying the agent's action model. Can be any function that takes an agent and a single input as arguments, and returns a probability distribution from which actions are sampled.
  * 'substruct::Any = nothing': struct containing additional parameters and states. This structure also get passed to utility functions. Check advanced usage guide.
  * 'parameters::Dict = Dict()': dictionary containing parameters of the agent. Keys are parameter names (strings, or tuples of strings), values are parameter values.
  * 'states::Union{Dict, Vector} = Dict()': dictionary containing states of the agent. Keys are state names (strings, or tuples of strings), values are initial state values. Can also be a vector of state name strings.
  * 'settings::Dict = Dict()': dictionary containing additional settings for the agent. Keys are setting names, values are setting values.
  * 'parameter_groups::Dict = Dict()': dictionary containing shared parameters. Keys are the the name of the shared parameter, values are the value of the shared parameter followed by a vector of the parameters sharing that value.

# Examples

```julia

## Create agent with a binary Rescorla-Wagner action model

## Create action model function

function binary*rescorla*wagner_softmax(agent::Agent, input::Union{Bool,Integer})

```
#Read in parameters
learning_rate = agent.parameters["learning_rate"]
action_precision = agent.parameters["action_precision"]

#Read in states
old_value = agent.states["value"]

#Sigmoid transform the value
old_value_probability = 1 / (1 + exp(-old_value))

#Get new value state
new_value = old_value + learning_rate * (input - old_value_probability)

#Pass through softmax to get action probability
action_probability = 1 / (1 + exp(-action_precision * new_value))

#Create Bernoulli normal distribution with mean of the target value and a standard deviation from parameters
action_distribution = Distributions.Bernoulli(action_probability)

#Update states
agent.states["value"] = new_value
agent.states["value_probability"], 1 / (1 + exp(-new_value))
agent.states["action_probability"], action_probability
#Add to history
push!(agent.history["value"], new_value)
push!(agent.history["value_probability"], 1 / (1 + exp(-new_value)))
push!(agent.history["action_probability"], action_probability)

return action_distribution
```

end

#Define requried parameters parameters = Dict(     "learning*rate" => 1,     "action*precision" => 1,     ("initial", "value") => 0, )

#Define required states states = Dict(     "value" => missing,     "value*probability" => missing,     "action*probability" => missing, )

#Create agent agent = init*agent(     binary*rescorla*wagner*softmax,     parameters = parameters,     states = states,     settings = settings, )
