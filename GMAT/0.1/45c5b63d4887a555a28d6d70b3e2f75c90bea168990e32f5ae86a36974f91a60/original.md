```
run_script(script;
	data=joinpath(artifact"data", "gmat-data-2020a"),
	output=joinpath(pwd(), "gmat-output"),
)
```

Run a GMAT `script` while optionally specifying the path to the `data` package and an `output` directory. The function will return a list of output files.

### References

  * [GMAT Documentation](http://gmat.sourceforge.net/docs/R2020a/html/index.html)
