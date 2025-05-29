```
enum_matcher(Enum, value)::Expr
```

Generates the expression used to test if `value` is the case `Enum`.

NOTE that this only works when `is_enum(Enum)` is `true`!!!

```
@match V begin
    Enum => ...
@end
```

Above single case matches when

1. `enum_matcher(Enum, ::Any)` is not defined and `V == Enum`.
2. The expression generated from `enum_matcher(Enum, :V)` evaluates to `true` under the current module.
