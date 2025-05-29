```
Actor - agent representing an economic actor.
```

# Fields

  * id::Int - the id of the agent.
  * types::Set{Symbol} - the types of the actor. Types are meant to be used in data collection and/or behavior functions.
  * model*behaviors::Vector{Function} - the list of functions which are called by econo*model*step!, which is the default model*step! function.
  * behaviors::Vector{Function} - the list of behavior functions which is called when the actor is activated.
  * balance::Balance - the balance sheet of the agent.
  * posessions::Entities - the entities in personal posession of the agent.
  * stock::Stock - the stock held by the agent. The stock is considered to be used for business purposes.
  * producers::Set{Producer} - the production facilities of the agent.
  * prices::D where D <: Dict{<:Blueprint, Price} - the prices of the products sold by the actor.
  * properties::Dict{Symbol, Any} - for internal use.

After creation, ant field can be set on the actor, even those which are not part of the structure. This can come in handy when when specific state needs to be stored with the actor.
