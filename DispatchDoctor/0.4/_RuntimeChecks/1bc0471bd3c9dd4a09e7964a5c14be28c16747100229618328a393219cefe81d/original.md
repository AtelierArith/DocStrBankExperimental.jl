```
allow_unstable(f::F) where {F<:Function}
```

Globally disable type DispatchDoctor instability checks within the provided function `f`.

This function allows you to execute a block of code where type instability checks are disabled. It ensures that the checks are re-enabled after the block is executed, even if an error occurs.

This function uses a `ReentrantLock` and will throw an error if used from two tasks at once.

# Usage

```
allow_unstable() do
    # do unstable stuff
end
```

# Arguments

  * `f::F`: A function to be executed with type instability checks disabled.

# Returns

  * The result of the function `f`.

# Notes

You cannot call `allow_unstable` from two tasks at once. An error will be thrown if you try to do so.
