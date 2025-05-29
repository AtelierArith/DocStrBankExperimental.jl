```
make_summary(
    prefix; 
    outputs=Outputs(json=JSONOutput(filename="summary.json"))
)
```

Combines multiple TMLE .hdf5 output files in a single file. Multiple formats can be output at once.

# Args

  * `prefix`: Prefix to .hdf5 files to be used to create the summary file

# Options

  * `-o, --outputs`: Ouptuts configuration.
