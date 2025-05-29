```
@RemoteFile name url [key=value...]
```

Assign the `RemoteFile` located at `url` to the variable `name`.

The following keyword arguments are available:

  * `file`: Set a different local file name.
  * `dir`: The download directory. If `dir` is not set RemoteFiles will create   a new directory `data` under the root of the current package and save the   file there.
  * `updates` (default: `:never`): Indicates with which frequency the   remote file is updated. Possible values are:

      * `:never`
      * `:daily`
      * `:monthly`
      * `:yearly`
      * `:mondays`/`:weekly`, `:tuesdays`, etc.
  * `retries` (default: 3): How many retries should be attempted.
  * `try_backends` (default: `true`): Whether to retry with different backends.
  * `backends` (default `RemoteFiles.BACKENDS`): Which backends to try.
  * `wait` (default: 5): How many seconds to wait between retries.
  * `failed` (default: `:error`): What to do if the download fails. Either throw   an exception (`:error`) or display a warning (`:warn`).
