```
BotConfig(package_name::AbstractString ; exclusions, os, else_os, version, else_version, package_path, precompiles_rootpath, subst, tmin)
```

Construct a SnoopCompile bot configuration. `package_name` is the name of the package. This object is passed to [`snoop_bot`](@ref) and [`snoop_bench`](@ref).

You may supply the following optional **keyword** arguments:

  * `exclusions` : A vector of of Strings (or RegExp) to exclude some functions from being precompiled
  * `os`: A vector of of Strings (or RegExp) to support with precompile statements.

Example: `os = ["windows", "linux"]`

  * `else_os`: If you want to use a specific operating system's precompile file as the default, set `else_os` to the name of that os. Not passing this argument skips precompilation on any operating system other than those explicitly listed in `os`.

Example: `else_os = "linux"`

  * `version`: A vector of of Julia versions used to generate precompile signatures.

Example: `version = [v"1.1", v"1.4.2", "nightly"]`

It is assumed that the generated precompile signatures are valid for patch versions of Julia (e.g. giving v"1.4.2" supports v"1.4.0" to v"1.4.9").

  * `else_version`: the Julia version used to generate the default signatures for other `version`s.

Not passing this argument skips precompilation on any Julia version other than those explicitly listed in `version`.

Example: `else_version = v"1.4.2"`

  * `yml_path`: instead of directly passing `os` and `version` to BotConfig, you can pass `yml_path` which should be the GitHub actions YAML path or file name.

It assumes that the job name is `SnoopCompile`.

Example: `yaml_path = "SnoopCompile.yml"`

  * `package_path`: path to the main `.jl` file of the package (similar to `pathof`). Default path is `pathof_noload(package_name)`.
  * `precompiles_rootpath`: the path where precompile files are stored. Default path is ":(dirname(dirname(package_path)))/deps/SnoopCompile/precompile".
  * `subst` : A vector of pairs of Strings (or RegExp) to replace a packages precompile statements with another's package like `["ImageTest" => "Images"]`.
  * `tmin`: Methods that take less time than `tmin` to be inferred will not be added to the precompile statements. Defaults to 0.
  * `check_eval`: By default, the bot discards the precompile statements that cannot be `eval`ed.

In rare cases (when snooping is very time consuming), you may want to do this manually by using the printed errors to add the problematic functions to `exclusions` and then set `check_eval=false` for the future runs.

# Example

```julia
botconfig1 = BotConfig(
  "Zygote";                            # package name (the one this configuration lives in)
  os = ["linux", "windows", "macos"],  # operating systems for which to precompile
  version = [v"1.4.2", v"1.3.1"],      # supported Julia versions
  exclusions = ["SqEuclidean"],         # exclude functions (by name) that would be problematic if precompiled
)

botconfig2 = BotConfig(
  "Zygote";                            # package name (the one this configuration lives in)
  yml_path = "SnoopCompile.yml"        # parse `os` and `version` from `SnoopCompile.yml`
  exclusions = ["SqEuclidean"],         # exclude functions (by name) that would be problematic if precompiled
)

# A full example:
BotConfig("MatLang", exclusions = ["badfunction"], os = ["linux", "windows", "macos"], else_os = "linux", version = ["1.4.2", "1.2", "1.0.5"], else_version = "1.4.2" )

# Different examples for other possibilities:
BotConfig("MatLang")

BotConfig("MatLang", exclusions = ["badfunction"])

BotConfig("MatLang", os = ["linux", "windows"])

BotConfig("MatLang", os = ["windows", "linux"], else_os = "linux")

BotConfig("MatLang", version = [v"1.1", v"1.4.2"])

BotConfig("MatLang", version = [v"1.1", v"1.4.2"], else_version = v"1.4.2")

BotConfig("MatLang", os = ["linux", "windows"], version = [v"1.1", v"1.4.2"])
```
