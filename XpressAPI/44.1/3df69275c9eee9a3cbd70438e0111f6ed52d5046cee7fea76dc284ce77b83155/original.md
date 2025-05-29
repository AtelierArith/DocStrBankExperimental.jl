```
XPRS_PREPROTECTDUAL
```

Presolve: specifies whether the presolver should protect a given dual solution by maintaining the same level of dual feasibility. (integer)

Enabling this control often results in a worse presolved model. This control only expected to be optionally enabled before calling `XPRScrossoverlpsol`.

Default value: `0`

Values: 0 : Disabled. 1 : Enabled. Protect the dual solution during presolve.
