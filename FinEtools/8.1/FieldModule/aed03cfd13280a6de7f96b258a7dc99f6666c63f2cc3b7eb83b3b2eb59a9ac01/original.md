```
numberdofs!(self::F, entperm) where {F<:AbstractField}
```

Number the degrees of freedom.

The free components in the field are numbered consecutively, then all the fixed components are numbered, again consecutively.

The sequence of the entities is given by the `entperm` permutation (array or range).
