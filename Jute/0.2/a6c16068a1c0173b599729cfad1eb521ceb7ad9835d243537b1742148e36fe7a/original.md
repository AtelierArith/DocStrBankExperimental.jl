```
@testcase [option=val ...] <name> begin ... end
@testcase [option=val ...] <name> for x in fx1, (y, z) in fx2 ... end
```

Create a testcase object and add it to the current test group.

Available options:

`tags :: Array{Symbol, 1}`: a list of tags for the testcase.
