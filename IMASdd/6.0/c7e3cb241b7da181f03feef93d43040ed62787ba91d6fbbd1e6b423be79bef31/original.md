```
getproperty(@nospecialize(ids::IDS), field::Symbol, @nospecialize(default::Any); to_cocos::Int=user_cocos)
```

Return IDS value for requested field or `default` if field is missing

NOTE: This is useful because accessing a `missing` field in an IDS would raise an error
