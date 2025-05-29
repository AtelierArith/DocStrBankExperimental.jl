```
@iso(using_or_import_statement)
@iso(using_or_import_statement, version_string)
```

Load a package or a package with a specified version. Currently, it does not support loading multiple packages at once.

# Examples

```
#Load Glob (after `IsoPkg.add("Glob")`)
@iso using Glob

#Load UnicodePlots v1.2.0 (after `IsoPkg.add("UnicodePlots@1.2.0")`)
@iso using UnicodePlots "1.2.0"
```

---

```
@iso(pkg_name, statement)
```

Run `statement` in the `pkg_name` environment.

# Examples

```
#Load Glob v1.2.0 (after `IsoPkg.add("Glob@1.2.0")`; equivalent to `@iso using Glob "1.2.0"`
@iso "Glob@1.2.0" using Glob

#Test Glob
@iso "Glob@1.2.0" Pkg.test("Glob")

#Show Glob status (equivalent to `IsoPkg.status("Glob@1.2.0")`)
@iso "Glob@1.2.0" pkg"status --manifest"
```
