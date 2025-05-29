```
@generate {<expression body>, <substitution ranges>, <local generator opts>} <generator opts>
@generate "{<<expression body>>, <substitution ranges>, <local generator opts>}" <generator opts>
```

Expand and evaluate parametrized expression comprehensions.

!!! When using the string form, an expression body containing a comma has to be escaped by another pair of angle brackets (`<` and `>`).

# Examples

```
@generate {$a+$b, a=1:3, b=3:5, dlm=+, zip=true} eval_macros=true
@generate "{$a+$b, a=1:3, b=3:5, dlm=+, zip=true}"
a=b=c=1; @generate {$[a,b,c], dlm=+}
a=b=c=1; @generate("{<$[a,b,c]>, dlm=+}")
```
