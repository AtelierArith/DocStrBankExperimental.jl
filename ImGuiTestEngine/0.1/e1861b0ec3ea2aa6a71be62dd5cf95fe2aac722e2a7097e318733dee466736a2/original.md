```julia
OpenAndClose(f, test_ref::Union{Int64, String})
OpenAndClose(f, test_ref::Union{Int64, String}, ctx)

```

A helper function that will ensure `test_ref` is open, execute `f()`, and close `test_ref` again. A typical use would be to open a section, run some tests, and then close the section again (handy for re-runnable tests).

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    OpenAndClose("My section") do
        # ...
    end
end
```
