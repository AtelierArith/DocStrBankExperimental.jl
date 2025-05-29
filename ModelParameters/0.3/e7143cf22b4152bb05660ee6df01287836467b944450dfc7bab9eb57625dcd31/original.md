```
withunits(object, [fieldname])
withunits(model::AbstractModel, [fieldname])
withunits(param::AbstractParam, [fieldname])
```

Returns the field specifed by `fieldname` (by default `:val`) for a single `Param`,  or a tuple of the `Param`s in a `Model` or arbitrary object. 

If there is a `units` field the returned value will be a combination of the specied field  and the `units` fields. 

If there is no units field or a specific `Param`s `units` fields contains `nothing`,  the field value is returned unchanged.
