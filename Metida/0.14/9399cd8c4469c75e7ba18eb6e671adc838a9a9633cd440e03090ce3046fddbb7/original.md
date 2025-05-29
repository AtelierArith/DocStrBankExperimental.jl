```
@lmmformula(formula, args...)
```

Macro for made formula with variance-covariance structure representation. `@lmmformula` could be used for shorter `LMM` construction.

Example:

```
lmm = Metida.LMM(@lmmformula(var~sequence+period+formulation,
random = formulation|subject:CSH,
repeated = formulation|subject:DIAG),
df0)
```

equal to:

```
lmm = LMM(@formula(var~sequence+period+formulation), df0;
random = VarEffect(@covstr(formulation|subject), CSH),
repeated = VarEffect(@covstr(formulation|subject), DIAG),
)
```

`@lmmformula` have 3 components - 1'st is a formula for fixed effect, it's defined like in `StstsModels` (1st argument just provided to `@formula` macro). Other arguments should be defined like keywords. `repeated` keyword define repeated effect part, `random` - define random effect part. You can use several random factors as in example bellow:

```
lmm = LMM(@lmmformula(var~sequence+period+formulation,
random = formulation|subject:CSH,
random = 1|subject:DIAG,
repeated = formulation|subject:DIAG),
df0)
```

`random` or `repeated` structure made by template:

`effect formula` | `blocking factor` [/ `nested factor`] [: `covariance structure`]

`|` - devide effect formula form blocking factor definition (necessarily), `/` and `:` modificator are optional.

`/` work like in MixedModels or in RegressionFormulae - expand factor `f|a/b` to `f|a` + `f|a&b`. It can't be used in repeated effect definition.

`:` - covariance structure defined right after `:` (SI, DIAG, CS, CSH, ets...), if `:` not used then SI used for this effect.

Terms like `a+b` or `a*b` shuould not be used as a blocking factors.
