```
C_iio_context_get_version(context)
```

Get the version of the backend in use.

# Parameters

  * `context::Ptr{iio_context}` : A pointer to an iio_context structure

# Returns

  * `ret::Int` : 0 if no errors, negative error code otherwise
  * `major::Int` : The major version
  * `minor::Int` : The minor version
  * `git_tag::String` : The git tag

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga342bf90d946e7ed3815372db22c4d3a6)
