The `@interval` macro converts an expression into a narrow interval that is guaranteed to contain the true value of the expression. When passed two expressions, it takes the hull of the resulting intervals to give a guaranteed containing interval.

Examples:

```
    @interval sin(0.1) + cos(0.2)
```

is equivalent to

```
    sin(0.1..0.1) + cos(0.2..0.2)
```

NOTE! `@interval` should be used only to create intervals from an expression, as in the example before. To construct an interval from single numbers, the `..` is preferred, e.g. `0.1..0.2`
