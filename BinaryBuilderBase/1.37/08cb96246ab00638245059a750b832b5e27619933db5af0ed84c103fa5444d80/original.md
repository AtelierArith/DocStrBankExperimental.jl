```
GitSource(url::String, hash::String; unpack_target::String = "")
```

Specify a remote Git repository to clone form `url`.  `hash` is the 40-character SHA1 revision to checkout after cloning.

The repository will be cloned in `${WORKSPACE}/srcdir`, or in its subdirectory pointed to by the optional keyword `unpack_target`, if provided.
