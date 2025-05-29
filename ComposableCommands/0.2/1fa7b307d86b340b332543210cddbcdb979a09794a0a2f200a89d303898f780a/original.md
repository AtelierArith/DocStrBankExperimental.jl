```
RedirectedCommand(source, destination)
```

Wrap an `AbstractCommand` and a file (`String`).

It allows output redirection from a command to a file or input redirection from a file to a command. The redirection is specified by the `RedirectedCommand`'s `source` and `destination` parameters.

# Arguments

  * `source`: The source from which to redirect. If `source` is a `String`, it represents the filename of the file from which to read. If `source` is a subtype of `AbstractCommand`, it represents the command whose output is to be redirected.
  * `destination`: The destination to which to redirect. If `destination` is a `String`, it represents the filename of the file to which to write. If `destination` is a subtype of `AbstractCommand`, it represents the command that takes the redirected output as input.
