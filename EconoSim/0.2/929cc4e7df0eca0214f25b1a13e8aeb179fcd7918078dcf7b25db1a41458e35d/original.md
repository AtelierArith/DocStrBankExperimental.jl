```
Actor - creation function for a generic actor.
```

# Parameters

  * id::Int = ID_COUNTER - the id of the agent. When no id is given, the standard sequence of id's is used. Mixing the standard sequence and user defined id's is not advised.
  * type::Union{Symbol, Nothing} = nothing - the types of the actor. Types are meant to be used in data collection and/or behavior functions.
  * model*behavior::Union{Function, Nothing} = nothing - the default function to be called by econo*model*step!, which is the default model*step! function.
  * behavior::Union{Function, Nothing} = nothing - the default behavior function which is called when the actor is activated.
  * balance::Balance = Balance() - the balance sheet of the agent.
  * posessions::Entities = Entities() - the entities in personal posession of the agent.
  * stock::Stock = Stock() - the stock held by the agent. The stock is considered to be used for business purposes.
  * producers::Union{AbstractVector{Producer}, AbstractSet{Producer}} = Set{Producer}() - the production facilities of the agent.
