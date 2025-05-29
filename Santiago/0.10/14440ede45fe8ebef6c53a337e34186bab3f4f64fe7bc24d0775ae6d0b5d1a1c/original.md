```
import_technologies(techFile::String, case_file::String;
                    sourceGroup::String="U", sourceAddGroup::String="Uadd",
                    sinkGroup::String="D")
```

Import a `json` file defining the technologies *and* a file defining the case. The latter is used to compute the appropriateness scores.

It returns i) array with sources, ii) array with additional sources, and iii) an array of all technologies with TAS scores.
