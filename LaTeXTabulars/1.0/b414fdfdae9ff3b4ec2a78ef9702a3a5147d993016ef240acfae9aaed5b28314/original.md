```julia
Rule()
Rule(kind)

```

Horizontal rule. The `kind` of the rule is specified by a symbol, which will generally be printed as `\KINDrule` for rules in `booktabs`, eg `Rule(:top)` prints `\toprule`. To obtain a `\hline`, use `Rule{:h}`.
