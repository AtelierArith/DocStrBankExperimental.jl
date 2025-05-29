function get_revisionIfAny( ctype::Type{CT}, rtype::Type{RT}, hid::DbId, vid::DbId, )::Vector{RT} where {CT<:Component,RT<:ComponentRevision}     retrieves the revision of the unique component of type CT in history hid if one exists as of version vid 

```
オプションの（ユニークな）コンポーネントは、vid以降のバージョンに対してリビジョンを持つ場合があります。そのような場合、正当なリビジョンを持たないコンポーネントはそれ自体が有効であり、現在のバージョンに対して無視されるだけです。
```
