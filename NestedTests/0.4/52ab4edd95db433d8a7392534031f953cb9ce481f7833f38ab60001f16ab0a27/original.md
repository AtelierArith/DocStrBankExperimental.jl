```
nested_test(name::String) do ... end
```

Run tests in a nested environment. The test can use any of the variables defined in its parent test(s). Any changes made to these variables will be isolated from other sibling nested tests in this level, but will be visible to descendant nested tests.
