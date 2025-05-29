```julia
from_json(
    io::Union{IO, String},
    ::Type{PowerSystems.System};
    runchecks,
    assign_new_uuids,
    kwargs...
) -> PowerSystems.System

```

assign*new*uuids = true の場合、システムおよびすべてのコンポーネントの新しい UUID を生成します。

警告: このメソッドでは時系列データは復元されません。必要な場合は、`System("sys.json")` のように、シリアライズされた JSON ファイルからシステムを構築する通常のプロセスを使用してください。
