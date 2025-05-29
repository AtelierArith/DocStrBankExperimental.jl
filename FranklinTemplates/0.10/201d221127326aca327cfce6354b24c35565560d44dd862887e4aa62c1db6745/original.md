```
newsite(topdir; template="basic", cd=true)
```

Generate a new folder (an error is thrown if it already exists) that contains the skeleton of a website that can be processed by Franklin. The user can specify a `template` out of the list of available templates. If `topdir` is specified as `"."` then the current directory is used.

  * `template="basic"`: name of the template to use,
  * `cd=true`:          whether to change the current directory to the newly                     created folder or not.
  * `verbose=true`:     whether to display information or not.

### Example

```julia
newsite("MyNewWebsite", template="pure-sm")
```
