```
numberdofs!(self::F) where {F<:AbstractField}
```

Number the degrees of freedom.

The free components in the field are numbered consecutively, then all the fixed components are numbered, again consecutively.

No effort is made to optimize the numbering in any way. If you'd like to optimize the numbering of the degrees of freedom, use a form that sets the permutation of the degrees of freedom, or the permutation of the nodes.
