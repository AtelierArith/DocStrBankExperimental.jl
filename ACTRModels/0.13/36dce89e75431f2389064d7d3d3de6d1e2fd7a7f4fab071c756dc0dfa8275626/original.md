```
function ACTR(;
    name="model1", 
    declarative=Declarative(), 
    imaginal=Imaginal(), 
    goal = Goal(), 
    scheduler=Scheduler(), 
    visual=nothing, 
    visual_location=nothing, 
    procedural=nothing, 
    motor=nothing, 
    visicon=init_visicon(), 
    parm_type = Parms, 
    rng = Random.default_rng(),
    parms...)
```

A constructor for creating an `ACTR` model object. 

# Keywords

  * `name`: model name
  * `declarative`: declarative memory module
  * `imaginal`: imaginal memory module
  * `visual`: visual module
  * `goal`: goal module
  * `visual_location`: visual location module
  * `visicon`: a vector of VisualObjects available in the task
  * `parms`: model parameters
  * `scheduler`: event scheduler
  * `rng': random number generator

# Example

```@example
using ACTRModels
parms = (noise=true, τ=-1.0)
chunks = [Chunk(;animal=:dog,name=:Sigma), Chunk(;animal=:rat,name=:Bonkers)]
declarative = Declarative(;memory=chunks)
actr = ACTR(;declarative, parms...)
```
