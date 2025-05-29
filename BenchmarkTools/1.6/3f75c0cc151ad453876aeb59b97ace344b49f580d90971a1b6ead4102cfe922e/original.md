```
@bprofile expression [other parameters...]
```

Run `@benchmark` while profiling. This is similar to

```
@profile @benchmark expression [other parameters...]
```

but the profiling is applied only to the main execution (after compilation and tuning). The profile buffer is cleared prior to execution.

View the profile results with `Profile.print(...)`. See the profiling section of the Julia manual for more information.
