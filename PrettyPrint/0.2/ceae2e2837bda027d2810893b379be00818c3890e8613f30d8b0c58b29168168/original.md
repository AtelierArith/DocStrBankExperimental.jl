The implementation of `pprint` and `pformat`.

You can extend pretty print support via such boilerplate:

```
    function PrettyPrint.pp_impl(io, data::YourType, indent::Int)
        print(io, data)
    end
```
