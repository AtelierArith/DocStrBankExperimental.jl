```
Scope(<keyword arguments>)
```

An object which can send and receive messages.

# Arguments

  * `dom`: The DOM node that will be rendered when the scope is displayed in the   browser.
  * `imports`: An collection of `Asset`s to load (see [`Asset`](@ref) for   more documentation) when the scope is mounted. If the entry is not an   `Asset` then it should be an argument to construct an `Asset`.

# Examples

```julia
myscope = Scope(
    dom=node(:p, "I'm a little scope!"),
    imports=[Asset("foo.js"), "bar.css", "spam" => "spam.js"],
)
```
