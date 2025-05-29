```
suggest_alternative_kws(kws, possible_kws; n_suggestions = 3, cutoff = 0.6)
```

Suggest alternative keywords, where `kws` is the list of keyword names passed to a function, and `possible_kws` is the list of true keyword names. These should be either symbols or strings. You can get this from the function `kws` by using `keys(kws)`.

# Examples

```julia
function f(; kws...)
    msg = suggest_alternative_kws(keys(kws), [:kw1, :kw2])
    if isempty(msg)
        return "all keywords are valid"
    else
        return "received some invalid keywords, here is the error:" * msg
    end
end
```
