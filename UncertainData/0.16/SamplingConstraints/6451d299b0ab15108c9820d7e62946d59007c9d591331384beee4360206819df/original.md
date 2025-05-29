Fallback constraints. This is necessary when sampling constraints are not compatible. For example, the `TruncatedStd` constraint is not implemented for `UncertainScalarKDE`, so we need a fallback.

The default is to fall back to `NoConstraint()``.
