```
evaluate_pp(pm, xp, yp, pp)
```

Evaluate field at position using horner scheme

  * pm : kernel smoother object
  * position : Position where to evaluate
  * field*dofs*pp(:,:) : Degrees of freedom in kernel representation.
  * field_value : Value of the field
