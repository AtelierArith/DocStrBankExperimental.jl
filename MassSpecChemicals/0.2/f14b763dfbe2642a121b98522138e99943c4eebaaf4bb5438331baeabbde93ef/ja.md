```
chemicalname(chemical::T; kwargs...)
```

`chemical`の名前を取得します。これは`getchemicalattr(chemical, :name; kwargs...)`と同等ですが、名前が利用できない場合は`string("::", T)`を返します。
