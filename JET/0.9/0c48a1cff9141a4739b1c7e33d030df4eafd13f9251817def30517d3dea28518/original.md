```
report_package(package::Module; jetconfigs...) -> JETToplevelResult
report_package(package::AbstractString; jetconfigs...) -> JETToplevelResult
```

Analyzes `package` in the same way as [`report_file`](@ref) and returns back type-level errors with the special default configurations, which are especially tuned for analyzing a package (see below for details). The `package` argument can be either a `Module` or a `AbstractString`. In the latter case it must be the name of a package in your current environment.

The error analysis performed by this function is configured as follows by default:

  * `analyze_from_definitions = true`: This allows JET to start analysis without top-level call sites. This is useful for analyzing a package since a package itself usually only contains definitions of types and methods but not their usages (i.e. call sites).
  * `concretization_patterns = [:(x_)]`: Concretizes every top-level code in a given `package`. The concretizations are generally preferred for successful analysis as far as they can be performed cheaply. In most cases it is indeed cheap to interpret and concretize top-level code written in a package since it usually only defines types and methods.
  * `ignore_missing_comparison = true`: JET ignores the possibility of a poorly-inferred comparison operator call (e.g. `==`) returning `missing`. This is useful because `report_package` often relies on poor input argument type information at the beginning of analysis, leading to noisy error reports from branching on the potential `missing` return value of such a comparison operator call. If a target package needs to handle `missing`, this  configuration shuold be turned off since it hides the possibility of errors that may actually at runtime.

See [`ToplevelConfig`](@ref) and [`JETAnalyzer`](@ref) for more details.

Still the [general configurations](@ref) and [the error analysis specific configurations](@ref jetanalysis-config) can be specified as a keyword argument, and if given, they are preferred over the default configurations described above.

---

```
report_package(; jetconfigs...) -> JETToplevelResult
```

Like above but analyzes the package of the current project.

See also [`report_file`](@ref).
