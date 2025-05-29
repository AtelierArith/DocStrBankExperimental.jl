A `FrameworkProduct` is a  [`Product`](@ref) that encapsulates a macOS Framework. It behaves mostly as a [`LibraryProduct`](@ref) for now, but is a distinct type. This implies that for cross-platform builds where a library is provided as a Framework on macOS and as a normal library on other platforms, two calls to BinaryBuilder's `build_tarballs` are needed: one with the `LibraryProduct` and all non-macOS platforms, and one with the `FrameworkProduct` and the `MacOS` platforms.

---

```
FrameworkProduct(fwnames, varname::Symbol)
```

Declares a macOS `FrameworkProduct` that points to a framework located within the prefix, with a name containing `fwname` appended with `.framework`.  As an example, given that `fwname` is equal to `QtCore`, this would be satisfied by the following path:

```
lib/QtCore.framework
```
