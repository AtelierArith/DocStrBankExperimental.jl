```
synth(problem::Problem, iterator::ProgramIterator; shortcircuit::Bool=true, allow_evaluation_errors::Bool=false, mod::Module=Main)::Union{Tuple{RuleNode, SynthResult}, Nothing}
```

Synthesize a program that satisfies the maximum number of examples in the problem. 		- problem                 - The problem definition with IO examples 		- iterator                - The iterator that will be used 		- shortcircuit            - Whether to stop evaluating after finding a single example that fails, to speed up the [synth](@ref) procedure. If true, the returned score is an underapproximation of the actual score. 		- allow*evaluation*errors - Whether the search should crash if an exception is thrown in the evaluation 		- max*time                - Maximum time that the iterator will run  		- max*enumerations        - Maximum number of iterations that the iterator will run  		- mod                     - A module containing definitions for the functions in the grammar that do not exist in Main

Returns a tuple of the rulenode representing the solution program and a synthresult that indicates if that program is optimal. `synth` uses `evaluate` which returns a score in the interval [0, 1] and checks whether that score reaches 1. If not it will return the best program so far, with the proper flag
