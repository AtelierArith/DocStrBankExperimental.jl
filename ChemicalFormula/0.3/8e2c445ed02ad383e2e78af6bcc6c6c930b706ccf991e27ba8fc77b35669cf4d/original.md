```
latex(formula, includecharge=true, form="formula")
```

Give a formula written in LaTeX, using the mhchem package. `includecharge` determines  whether the electronic charge should be given, defaults to `true`. `form` has to be one of  `"formula"` (the `formula` that was given to construct the `Formula` object), `"hill"` or  `"hillformula"` for Hill notation or `"sum"` or `"sumformula"` for a collapsed sum  formula, defaults to `"formula"`.
