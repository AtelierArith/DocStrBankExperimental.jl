```
LLMOperationWeights(;kws...)
```

Defines the probability of different LLM-based mutation operations. NOTE: The LLM operations can be significantly slower than their symbolic counterparts, so higher probabilities will result in slower operations. By default, we set all probs to 0.0. The maximum value for these parameters is 1.0 (100% of the time).

# Arguments

  * `llm_crossover::Float64`: Probability of calling LLM version of crossover.
  * `llm_mutate::Float64`: Probability of calling LLM version of mutation.
  * `llm_gen_random::Float64`: Probability of calling LLM version of gen_random.
