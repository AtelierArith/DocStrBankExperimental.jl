```
set_infinite_domain(pref::GeneralVariableRef, domain::InfiniteScalarDomain)::Nothing
```

Specify the scalar infinite domain of the infinite parameter `pref` to `domain`. Note this will reset/delete all the supports contained in the underlying parameter object. Also, errors if `pref` is used by a measure. An `ArgumentError` is thrown if `pref` is not an infinite parameter.
