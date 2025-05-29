```
process_folder(folder="src") -> Vector{FileCoverage}
```

Process the contents of a folder of Julia source code to collect coverage statistics for all the files contained within. Will recursively traverse child folders. Default folder is "src", which is useful for the primary case where CoverageTools is called from the root directory of a package.
