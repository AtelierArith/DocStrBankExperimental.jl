```
req = @request expr
```

Create a request of internal results wanted from a function. Considering the function presented as example for [`@espy`](@ref), examples of possible syntax include

```
req       = @request gp[].(s,z,material.(a,b))
req       = @request gp[].(s)
req       = @request gp[].(material.(a))
```

The first expression can be read as follows: "In the function, there is a `for` loop over variable `igp`, and the results are wanted as a vector (one element for each cycle of the loop).  Each element of the vector shall be a `type` (a structure) with a field `material`, because a function of that name is called in the for loop.  Within that function, a variable `a` is to be retrieved.

Note the need to use parentheses also for single-element lists, as in `(s)`.

See also: [`@espy`](@ref), [`@espydbg`](@ref), [`makekey`](@ref)
