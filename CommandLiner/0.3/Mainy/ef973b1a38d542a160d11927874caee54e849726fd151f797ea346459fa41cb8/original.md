```
@main, @mn
@ismain
@guard
```

Main guard helpers:

  * `@main`: if run as script, calls the `main` function (which the user needs to provide).
  * `@mn`: same, but calls a (user-provided) `mn` function (for compat., should Julia handle `main` in the future).
  * `@ismain`: returns boolean; usage: `@ismain()  &&  myfunction()`.
  * `@guard`: shorter; usage: `@guard myfunction()`.

`@main` and `@mn` additionally wrap the main call in `hushexit`, which handles SIGPIPEs and iterrupts.

Also see: `hushexit`. 
