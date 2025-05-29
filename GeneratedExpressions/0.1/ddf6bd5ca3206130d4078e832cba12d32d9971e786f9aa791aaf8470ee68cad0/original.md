```
generate(body, pre_substitution; eval_module, tl_opts)
```

Expand and evaluate parametrized expression comprehensions.

!!! Note that in expressions, `$sym``atoms have to be escaped as`:(:sym)`.

# Examples

```
generate("{$a+$b, a=1:3, b=3:5, dlm=+, zip=true}")
generate(:({:($a)+:($b)+:($c), a=1:3, b=3:5, dlm=+, zip=true}), Dict(:c=>2))
```
