```
new_FISHfolder(newroot::String, oldroot::String, rep::String)
```

Creates a new folder structure for FISH data based on an existing structure.

# Arguments

  * `newroot`: The root directory for the new folder structure.
  * `oldroot`: The root directory of the existing folder structure.
  * `rep`: The string to search for in directory names.

# Description

This function walks through the existing folder structure and creates a new folder structure in the specified new root directory. It searches for directories containing the specified string and replicates their structure in the new root directory.
