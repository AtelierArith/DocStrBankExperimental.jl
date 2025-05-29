```
check_variable_links(model, modeldata; [throw_on_error=true] [, expect_hostdep_varnames=["global.tforce"]]) -> links_ok::Bool
```

Check all Variables linked correctly, by checking that there are no unexpected host-dependent non-state Variables (ie unlinked Variables)
