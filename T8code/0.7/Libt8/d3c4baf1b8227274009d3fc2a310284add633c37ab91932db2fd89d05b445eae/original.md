```
t8_cmesh_set_profiling(cmesh, set_profiling)
```

Enable or disable profiling for a cmesh. If profiling is enabled, runtimes and statistics are collected during cmesh_commit.

Profiling is disabled by default. The cmesh must not be committed before calling this function.

# Arguments

  * `cmesh`:[in,out] The cmesh to be updated.
  * `set_profiling`:[in] If true, profiling will be enabled, if false disabled.

# See also

[`t8_cmesh_print_profile`](@ref)

### Prototype

```c
void t8_cmesh_set_profiling (t8_cmesh_t cmesh, int set_profiling);
```
