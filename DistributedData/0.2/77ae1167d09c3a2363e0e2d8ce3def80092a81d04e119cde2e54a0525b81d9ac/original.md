```
@remote expr
```

In a function that will get evaluated on a remote worker, this ensures the evaluation scope of the expression `expr` (usually a variable) is taken on the remote side, preventing namespace clash with the local session.

This is mainly useful for making the functions from `Distributed` package (such as `pmap` and `remotecall`) work with the data stored by `DistributedData` package.

Internally, this is handled by wrapping in `eval`.

# Example

```
julia> save_at(2, :x, 321)
Future(2, 1, 162, nothing)

julia> let x=123
         remotecall_fetch(() -> x + (@remote x), 2)
       end
444
```
