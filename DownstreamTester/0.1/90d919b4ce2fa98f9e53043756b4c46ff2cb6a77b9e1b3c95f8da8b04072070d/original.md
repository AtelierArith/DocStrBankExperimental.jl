```
nightly(configfile::String = "DownstreamTester.json"; do_clone::Bool = true, nightlylabels::Vector{String} = ["nightly"])
```

Perform a nightly test on the Julia Package given in the config file. This function is aimed to be run daily in a scheduled GitHub action  to find and report on new test failures with the nightly version of Julia. When called it will clone the HEAD revision of the package repository  provided in the config and run the full testsuite on it.  If new failing tests are found it will open an issue on the package repository. If tests are passing it will report on the related issue and close it if all reported tests therein pass.
