```
cos(a::CalciumFieldElem; form::Symbol=:default)
```

Return the cosine of `a`. The optional `form` argument allows specifying the representation. In `:default` form, the result is determined by the `:trig_form` option of the parent object. In `:exponential` form, the value is represented using complex exponentials. In `:tangent` form, the value is represented using tangents. In `:direct` form, the value is represented directly using a sine or cosine.
