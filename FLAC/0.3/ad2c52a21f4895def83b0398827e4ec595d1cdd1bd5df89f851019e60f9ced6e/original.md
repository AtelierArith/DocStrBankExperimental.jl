```
initfile!(dd::StreamDecoderPtr, fnm::String; wcallback=debug_wcallback_c,
    mcallback=debug_mcallback_c, ecallback=debug_ecallback_c, client_data=nothing)
```

Initialize the `StreamDecoderPtr`, `dd`, to read the FLAC file `fnm`.

This function allows the user to override any of the default callback functions.
