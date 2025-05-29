```
CrossPlatform(host::Platform, target::Platform)
```

A special platform to be used when building cross-compiling toolchains; it contains a `host` platform and a `target` platform.  Both platforms are preserved through encoding one of the platforms into tags (e.g. by adding a prefix to the set of tags, a la `target_arch=x86_64`, `target_os=windows`, etc...).

We also support setting the `host` or `target` as an `AnyPlatform`, allowing the creation of any-host but target-specific binaries (such as `LinuxKernelHeaders_jll`) or host- specific but any-target binaries (such as certain builds of `Clang_jll`).  In order to properly lower this `Platform` to a serialized representation (both in text as well as an `Artifacts.toml` file) we must determine ways to properly encode the `host` and `target` platforms while maintaining the overall serialization as one that is parseable as the basic `Platform` type.  To this end, we generally choose the `host` as the "base" platform, then encode the `target` within the tags, except when the `host` is an `AnyPlatform`, in which case we flip and use the `target` as the "base" platform.  To disambiguate these two cases, we set the sentinel tag `target=any` for when the `target` is an `AnyPlatform`, and `host=any` for when the `host` is an `AnyPlatform`.  Because of these two tags, all valid `CrossPlatform` objects are identifiable by the presence of these tags (or the equally-identifiying `target_arch`/`host_os` etc... tags).

In the event that you try to turn a "normal" `Platform` object into a `CrossPlatform`, it will return a `CrossPlatform` object that has `host` and `target` equal to eacother.
