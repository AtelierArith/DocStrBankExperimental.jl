```
numberdofs!(self::F, entperm, kinds) where {F<:AbstractField}
```

Number the degrees of freedom.

# Arguments

  * `self::F`: The field object.
  * `entperm`: The permutation of entities.
  * `kinds`: The kinds of degrees of freedom. The degrees of freedom are numbered in the order in which the kinds are given here.

# Examples
