function get_revisionIfAny(rtype::Type{RT}, hid::DbId, vid::DbId, )::Vector{RT} where {RT<:ComponentRevision}     retrieves the revision of component cid if one exists as of version vid 

```
オプションのコンポーネントは、vid以降のバージョンに対してリビジョンを持つ場合があります。そのような場合、正当なリビジョンを持たないコンポーネントは、現在のバージョンに対して無視されるだけで、自己が有効です。
```
