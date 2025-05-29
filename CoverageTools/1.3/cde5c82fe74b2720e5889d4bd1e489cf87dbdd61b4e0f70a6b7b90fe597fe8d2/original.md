FileCoverage

Represents coverage info about a file, including the filename, the source code itself, and a `Vector` of run counts for each line. If the line was expected to be run the count will be an `Int` >= 0. Other lines such as comments will have a count of `nothing`.
