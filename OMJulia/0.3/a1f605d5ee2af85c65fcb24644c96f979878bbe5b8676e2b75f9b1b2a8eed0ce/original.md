```
sendExpression(omc, expr; parsed=true)
```

Send API call to OpenModelica ZMQ server. See [OpenModelica User's Guide Scripting API](https://openmodelica.org/doc/OpenModelicaUsersGuide/latest/scripting_api.html) for a complete list of all functions.

!!! note
    Some characters in argument `expr` need to be escaped. E.g. `"` becomes `\"`. For example scripting API call

    ```modelica
    loadFile("/path/to/M.mo")
    ```

    will translate to

    ```julia
    sendExpression(omc, "loadFile(\"/path/to/M.mo\")")
    ```


!!! warn
    On Windows path separation symbol `\` needs to be escaped `\\` or replaced to Unix style path `/` to prevent warnings.

    ```modelica
    loadFile("C:\\path\\to\\M.mo")
    ```

    translate to

    ```julia
    sendExpression(omc, "loadFile(\"C:\\\\path\\\\to\\\\M.mo\")")  # Windows
    sendExpression(omc, "loadFile(\"/c/path/to/M.mo\")")           # Windows
    ```


## Example

```julia
using OMJulia
omc = OMJulia.OMCSession()
OMJulia.sendExpression(omc, "getVersion()")
```
