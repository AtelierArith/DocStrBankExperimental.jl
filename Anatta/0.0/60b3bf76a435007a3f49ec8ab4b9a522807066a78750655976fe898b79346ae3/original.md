```
Activity
```

A single activity to be performed and responded to by the learner. An Activity is the basic unit of learning in Anatta. It contains ... 

# Fields

  * `prompt`	: Text prompting an activity by the learner.
  * `hint`	: Text suggesting to the learner how to respond to the prompt.
  * `success`	: Boolean function that defines the criteria for a successful learner response.

# Examples

```julia
julia> act = Anatta.Activity( "What is 2+3?", "Add the numbers together", x -> x==5)
Anatta.Activity("What is 2+3?", "Add the numbers together", var"#5#6"())

julia> act.success(5)
true
```
