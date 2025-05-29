```
newsite(topdir; template="basic", cd=true)
```

Generate a new folder (an error is thrown if it already exists) that contains the skeleton of a website that can be processed by JuDoc. The user can specify a `template` out of the list of available templates.

  * `template="basic"` specify the name of the desired template,
  * `cd=true` specify whether to change the current directory to the newly created folder or not.
  * `verbose=true` specify whether to display information or not.

### Example

```julia
newsite("MyNewWebsite", template="pure-sm")
```
