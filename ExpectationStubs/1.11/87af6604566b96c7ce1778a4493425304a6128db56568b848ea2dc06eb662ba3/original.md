```
@stub(name)
```

Declares that you will be making a stub function called `name`. The key difference between a stub and a julia function, is that stubs can have values for arguements declared, which must match, as well as having types which must match. Also they are simpler, in that they can not varying their return result based on argument.

Once you have declared a stub, you should use `@expect` to declare what it should respond to.

Calling methods that do not exist (with values provided), will result in Errors. This is intentional, as the stub exists to check that your function is only called with the arguements that you say are valid.
