```
testprogram()
```

Identify the test program file.

In an interactive session, or if `PROGRAM_FILE` is empty, the program file is the file from which testprogram()'s caller was called. otherwise, the program file is the value of `PROGRAM_FILE`.

For example, if `test/runtests.jl` calls `runtests` and then `runtests` calls `testprogram`:

  * In an interactive session, the program file is `test/runtests.jl`.
  * If `PROGRAM_FILE` is empty, the program file is `test/runtests.jl`.
  * If `PROGRAM_FILE` is not empty in a non-interactive session, the program file is the value of `PROGRAM_FILE`.
