```julia
close(trajectory::Chemfiles.Trajectory)

```

Close a `trajectory`. This function flushes any buffer content to the hard drive, and frees the associated memory. Necessary when running on the REPL to finish writing.
