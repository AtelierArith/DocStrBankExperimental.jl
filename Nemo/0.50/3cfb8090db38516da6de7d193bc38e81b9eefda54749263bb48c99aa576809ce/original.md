```
conj(a::CalciumFieldElem; form::Symbol=:default)
```

Return the complex conjugate of `a`. The optional `form` argument allows specifying the representation. In `:shallow` form, $\overline{a}$ is introduced as a new extension number if it no straightforward simplifications are possible. In `:deep` form, complex conjugation is performed recursively.
