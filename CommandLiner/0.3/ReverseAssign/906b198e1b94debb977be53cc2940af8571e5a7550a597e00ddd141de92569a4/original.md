```
1.0 |> sin |> cos |> sin |> :mynewvariable
```

After calling `ReverseAssign.enable()`, you can reverse-assign into a variable (its name given by the symbol to the right).

Meant to be used in the REPL. This hack avoids having to go back at the start of a REPL pipeline to enter some `x =` there.

  * The new variable lives in the `Main` scope.
  * This works by overwriting the function call operator for `Symbol`.
