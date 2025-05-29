Special if_else to use for conditionals instead of builtin ifelse because the latter evaluates all its arguments. Many ifelse statements are used as guards against computations that would cause an exception so need a new version that is transformed into 

`condition ? true_branch : false_branch`

during code generation.
