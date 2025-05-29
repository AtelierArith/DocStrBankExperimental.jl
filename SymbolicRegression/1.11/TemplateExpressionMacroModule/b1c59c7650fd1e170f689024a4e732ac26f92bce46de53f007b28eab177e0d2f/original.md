```
@template_spec(
    expressions=(f, g, ...),
    [parameters=(p1=size1, p2=size2, ...)],
    [num_features=(f=n1, g=n2, ...)]
) do x1, x2, ...
    # template function body
end
```

Creates a TemplateExpressionSpec with a custom template structure for symbolic regression.

This macro allows defining structured symbolic expressions with constrained composition of sub-expressions and parameterized components.

# Arguments

  * `expressions`: A tuple of function names that will be composed in the template.
  * `parameters`: Optional. A named tuple of parameter name-size pairs. These parameters   can be indexed and accessed in the template function.
  * `num_features`: Optional. A named tuple specifying how many features each expression function can access.   Normally this will be inferred automatically from the template function.

# Example

```julia
expr_spec = @template_spec(
    parameters=(p1=10, p2=10, p3=1),
    expressions=(f, g),
) do x1, x2, class
    return p1[class] * g(x1^2) + f(x1, x2, p2[class]) - p3[1]
end
```
