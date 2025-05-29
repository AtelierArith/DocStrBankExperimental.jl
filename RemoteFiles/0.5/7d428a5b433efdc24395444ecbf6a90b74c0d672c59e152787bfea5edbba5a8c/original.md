```
RemoteFile(uri::URI; kwargs...)
```

Create a `RemoteFile` instance with location `url`.

The following keyword arguments are available:

  * `file`: Set a different local file name.
  * `dir`: The download directory. If `dir` is not set RemoteFiles will create   a new directory `data` in the current directory, i.e. at `pwd()`.
  * `updates` (default: `:never`): Indicates with which frequency the   remote file is updated. Possible values are:

      * `:never`
      * `:daily`
      * `:monthly`
      * `:yearly`
      * `:mondays`/`:weekly`, `:tuesdays`, etc.
  * `retries` (default: 3): How many retries should be attempted.
  * `try_backends` (default: `true`): Whether to retry with different backends.
  * `wait` (default: 5): How many seconds to wait between retries.
  * `failed` (default: `:error`): What to do if the download fails. Either throw   an exception (`:error`) or display a warning (`:warn`).

Note: the difference to `@RemoteFile` is that the default directory `data` is created in `pwd()` as opposed to a under the root of the current package.
