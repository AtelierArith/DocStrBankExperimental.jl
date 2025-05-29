```
@template_spec(
    parameters=(p1=10, p2=10, p3=1),
    expressions=(f, g),
) do x1, x2, class
    return p1[class] * g(x1^2) + f(x1, x2, p2[class]) - p3[1],
end
```

(Experimental) Creates a TemplateExpressionSpec with the given parameters and expressions. The parameters are used to define constants that can be indexed, and the expressions define the function keys for the template structure.
