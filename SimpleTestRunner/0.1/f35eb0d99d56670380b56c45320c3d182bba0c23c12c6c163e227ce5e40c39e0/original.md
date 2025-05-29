```
runtests(args::Vector{String}=ARGS; io::IO=stdout, progname::String=testprogram())
```

Run tests from some or all test files in a test directory tree.

The root of the tree is taken as the directory in which `progname` exists.

The list of test names is taken from `ARGS` if `ARGS` is non-empty, otherwise from calling `testnames` for the root of the tree.

The list of test names is then used to construct test file names that are included into module `Main` with `Base.include`, each include wrapped in its own `@testset`.
