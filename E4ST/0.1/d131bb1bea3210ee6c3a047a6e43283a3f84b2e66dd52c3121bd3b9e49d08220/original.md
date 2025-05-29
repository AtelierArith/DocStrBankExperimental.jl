```
function add_obj_exp!(data, model, term::Term, s::Symbol; oper)
```

Adds expression s (already defined in model) to the objective expression model[:obj].  Adds the name, oper, and type of the term to data[:obj_vars].
