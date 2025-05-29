```
user_function(enter)
```

Emit an event into the tracefile which references the source code (data includes: source line number, file name and function name).

If enter is 0 it marks an end (i.e., leaving the function), otherwise it marks the beginning of the routine. The user must be careful to place the call of this routine in places where the code is always executed, being careful not to place them inside if and return statements. The function returns the address of the reference.

```julia
function routine1()
    user_function(1);
    [routine1 code]
    user_function(0);
end

function routine2()
    user_function(1);
    [routine2 code]
    user_function(0);
end
```

In order to gather performance counters during the execution of these calls, the user-functions tag and its counters have to be both enabled int section.

# Warning

Note that you need to compile your application binary with debugging information (typically the `-g` compiler flag) in order to translate the captured addresses into valuable information such as function name, file name and line number.
