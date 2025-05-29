```
RestrictedInteractionTransformer(;order=2, primary_variables=Symbol[], primary_variables_patterns=Regex[])
```

# Definition

This transformer generates interaction terms based on a set of primary variables. All generated interaction terms  are composed of a set of primary variables and at most one remaining variable in the provided table. If (T₁, T₂) are defining the set of primary variables and (W₁, W₂) are reamining variables in the table, the generated interaction terms at order 2  will be:

  * T₁xT₂
  * T₁xW₂
  * W₁xT₂

but W₁xW₂ will not be generated because it would contain 2 remaining variables.

# Arguments:

  * order: All interaction features up to the given order will be computed
  * primary_variables: A set of column names to generate the interactions
  * primary*variables*patterns: A set of regular expression that can additionally

be used to identify primary_variables.
